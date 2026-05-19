## 1. Introduction

Disk and file encryption protect data at rest by converting plaintext into ciphertext using cryptographic algorithms. Encryption ensures that unauthorized users—particularly in scenarios involving physical access or compromised systems—cannot read sensitive data. The implementation of encryption varies in scope and depth: full disk, partition-level, volume-level, or file-level encryption.

Understanding the technical nuances, attack vectors, and security architecture associated with each encryption level is critical for defending against advanced threats.

---

## 2. Full Disk Encryption (FDE)

### 2.1 Description

Full Disk Encryption encrypts the entire contents of a physical disk, including:

- System files
    
- Metadata (e.g., MFT, partition tables)
    
- Swap and hibernation files (depending on configuration)
    
- Free/unallocated space
    

FDE typically requires pre-boot authentication to unlock the disk. It ensures that the operating system and user data remain encrypted while the system is powered off.

### 2.2 Tools and Standards

- **BitLocker (Microsoft)** – Uses AES-XTS with 128- or 256-bit keys; integrates with TPM for key storage.
    
- **FileVault 2 (macOS)** – Uses XTS-AES-128 with 256-bit keys.
    
- **LUKS/dm-crypt (Linux)** – Follows specifications under [cryptsetup](https://gitlab.com/cryptsetup/cryptsetup); supports PBKDF2 and Argon2i/2id.
    
- **SEDs (Self-Encrypting Drives)** – Implement Opal SSC by the Trusted Computing Group (TCG); hardware encryption.
    

### 2.3 Threat Model and Security Considerations

|Threat|Mitigation|
|---|---|
|Physical theft|Enforced encryption with strong authentication (TPM + PIN or passphrase)|
|Cold boot attacks|Disable sleep/hibernate; use memory scrubbing on shutdown|
|Evil maid attacks|Utilize tamper detection, boot verification, measured boot (Intel TXT/TPM PCR)|
|Bootkits|Secure Boot, TPM binding, signed bootloaders|
|Direct Memory Access (DMA)|Enable IOMMU/VT-d (Intel) or AMD-Vi; disable unused ports|

**Note:** FDE does not protect against malware or privilege escalation once the system is booted and decrypted.

---

## 3. Partition Encryption

### 3.1 Description

Partition-level encryption allows specific logical sections of a disk (boot, system, data) to be encrypted or left in plaintext. This approach is useful when balancing performance, accessibility, and data confidentiality.

Each partition can be encrypted with a different key and policy. For example, only the data partition may be encrypted, leaving system partitions in plaintext for faster booting and compatibility with recovery tools.

### 3.2 Use Cases

- Mobile devices with separate partitions for OS and user data.
    
- Dual-boot environments.
    
- Cloud VMs with encrypted ephemeral storage.
    

### 3.3 Considerations

- Ensure unencrypted partitions do not leak sensitive data (e.g., logs, temp files).
    
- Partition table leakage: GPT or MBR is usually unencrypted and may reveal volume layouts and OS type.
    

---

## 4. Volume Encryption

### 4.1 Description

A volume is a logical storage entity with a single file system, potentially spanning multiple physical disks (e.g., LVM, RAID). Volume encryption encrypts all content within that volume.

This level of encryption is often implemented via the operating system or third-party software.

### 4.2 Notable Implementations

- **BitLocker To Go**: For external drives.
    
- **VeraCrypt**: Successor to TrueCrypt; supports plausible deniability and hidden volumes.
    
- **ZFS Native Encryption**: Provides dataset-level encryption using per-dataset keys.
    

### 4.3 Vulnerabilities and Considerations

- Mount-time decryption: Once mounted, data is available to the OS and any privileged process.
    
- Key exposure in memory: Encryption keys and decrypted content can be scraped from RAM by post-exploitation tools (e.g., Mimikatz, Volatility).
    
- Volume headers: If not stored securely, headers may reveal key derivation parameters or salt.
    

---

## 5. File and Directory Encryption

### 5.1 Description

File-level encryption applies encryption policies to individual files or directories. This allows for selective encryption, finer access control, and per-user confidentiality.

### 5.2 Tools

- **EFS (Encrypting File System)** – Available in Windows NTFS. Uses per-file symmetric encryption keys protected by the user’s public key.
    
- **GnuPG (GPG)** – Open-source tool for encrypting files using symmetric or asymmetric keys.
    
- **eCryptfs** – Stacked cryptographic file system for Linux; used by Ubuntu's encrypted home directories.
    

### 5.3 Threats

- Plaintext leakage during temporary storage or backups.
    
- Metadata exposure: file names, timestamps, and permissions are usually left in plaintext.
    
- Local privilege escalation may allow attackers to access decrypted files in memory or cache.
    

### 5.4 Forensics Implication

Encrypted files, once opened, may be cached by the OS (in swap, temp, or journal files). A forensic analyst may retrieve partial content if proper secure deletion is not used.

---

## 6. Encryption Metadata and Unallocated Space

### 6.1 Metadata

- File metadata includes creation/modification dates, file ownership, ACLs, and extended attributes.
    
- Many encryption systems (especially at the file level) do not encrypt metadata.
    
- Tools like `stat`, `ls -l`, or `Get-Item` in PowerShell can reveal information about encrypted files.
    

### 6.2 Unallocated Space

- Deleted files may leave remnants in unallocated space unless securely wiped.
    
- Disk forensics tools such as The Sleuth Kit or X-Ways can recover deleted files unless full-disk encryption includes free space.
    

### 6.3 Mitigation

- Enable full disk encryption with unallocated space encryption.
    
- Use tools like `sdelete` (Windows), `shred` (Linux), or `wipe`.
    
- For SSDs, TRIM must be handled cautiously; some SSDs do not encrypt TRIM-cleared blocks reliably.
    

---

## 7. Hardware Key Storage: TPM and HSM

### 7.1 TPM (Trusted Platform Module)

- Onboard secure crypto-processor tied to the motherboard.
    
- Stores disk encryption keys, measurements of boot state (PCR registers).
    
- Supports binding and sealing operations, remote attestation.
    

**Relevant Standards:**

- TPM 2.0 (ISO/IEC 11889)
    
- TCG PC Client Platform Firmware Profile
    

### 7.2 HSM (Hardware Security Module)

- Enterprise-grade hardware device for managing cryptographic keys.
    
- Typically deployed in PKI, database encryption, and cloud services (e.g., AWS CloudHSM).
    
- Can enforce access policies, audit logging, and prevent key extraction.
    

---

## 8. Adversarial Considerations (Red Team / Black Hat)

### 8.1 Reconnaissance Phase

- Enumerate encryption tools in use via OS artifacts (e.g., BitLocker status via `manage-bde`, LUKS headers).
    
- Dump GPT/MBR to analyze partition schemes.
    
- Check for unlocked or auto-mounted volumes.
    

### 8.2 Exploitation Phase

- Use DMA-based attacks with PCILeech or Inception if physical access is available.
    
- Perform cold boot to recover keys from DRAM (e.g., via volatility).
    
- Inject bootkit to capture passphrase at pre-boot (evil maid scenario).
    
- Exploit recovery key mismanagement (e.g., stored in AD, leaked in plaintext logs).
    
- Abuse plaintext or insufficiently secured configuration files that store decryption secrets.
    

---

## 9. Defensive Best Practices

|Control|Recommendation|
|---|---|
|Encryption scope|Apply full disk encryption including free space and swap|
|Authentication|Require multifactor pre-boot auth with TPM binding|
|Secure boot|Enable UEFI Secure Boot and kernel integrity enforcement|
|Key management|Use centralized key lifecycle management (e.g., Vault, AWS KMS)|
|Memory protection|Lock keys in TPM or HSM; scrub RAM on shutdown|
|Logging|Enable audit logs for decryption, key access, and volume mounting|

---

## 10. References

- NIST SP 800-111: Guide to Storage Encryption Technologies
    
- NIST SP 800-57: Key Management Guidelines
    
- ISO/IEC 27040: Storage Security
    
- [Microsoft BitLocker Deployment Guide](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview)
    
- [Linux dm-crypt / LUKS documentation](https://gitlab.com/cryptsetup/cryptsetup)
    
- [IEEE 1619-2007 XTS-AES Standard](https://standards.ieee.org/ieee/1619/3603/)
    
- Trusted Computing Group (TCG) Opal Specification
    
- SED vulnerabilities