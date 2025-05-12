### Overview

Transport encryption refers to the cryptographic processes used to **secure data in transit**—i.e., data that is moving between systems across potentially insecure networks (e.g., LANs, the Internet). Its core goals are:

- **Confidentiality** – Prevent eavesdropping.
    
- **Integrity** – Prevent unauthorized modification.
    
- **Authentication** – Verify the identity of communicating parties.
    
- **Forward Secrecy** – Ensure past sessions remain confidential even if long-term keys are compromised.
    

Due to performance considerations, **hybrid cryptographic systems** are used. Asymmetric cryptography facilitates **key exchange**, while **symmetric cryptography** encrypts the payload.

![[Pasted image 20250513032546.png]]

---

### Protocols and Use Cases

|Protocol|Layer|Description|Use Case|
|---|---|---|---|
|**WPA2/WPA3**|Data Link|Implements AES-CCMP (WPA2) or SAE (WPA3) for encrypting Wi-Fi traffic.|Wireless LAN security|
|**IPsec**|Network|Encrypts IP packets at the OSI Layer 3; uses ESP or AH headers. Supports transport and tunnel modes.|VPNs, site-to-site or host-to-site tunnels|
|**TLS (1.2/1.3)**|Application|Protocol-independent secure transport layer. Wraps protocols like HTTP, SMTP, IMAP. TLS 1.3 removes legacy flaws.|HTTPS, secure email, VoIP|
|**SSH**|Application|Encrypts remote shell, SCP, SFTP; uses Diffie-Hellman key exchange and public key authentication.|Secure remote access|

---

### Cryptographic Process: Hybrid Encryption Model

Hybrid encryption combines the **efficiency of symmetric encryption** with the **security of public key cryptography**. Transport encryption implementations use **ephemeral session keys** derived and exchanged securely.

#### General Workflow:

```
1. Client requests secure communication (e.g., TLS handshake).
2. Server presents digital certificate containing its public key. 
3. Client verifies certificate via a trusted Certificate Authority (CA). 
4. Client generates a symmetric session key (e.g., 256-bit AES key). 
5. Client encrypts session key using the server’s public key (RSA/ECC). 
6. Encrypted session key is sent to server. 
7. Server decrypts it with its private key to retrieve the session key. 
8. Both sides now use the shared symmetric session key for encrypting data.
```


In **TLS 1.3**, RSA key exchange is deprecated. Instead, **ephemeral Elliptic Curve Diffie-Hellman (ECDHE)** is used to provide **Forward Secrecy**.

---

### Key Exchange Algorithms

|Algorithm|Type|Characteristics|
|---|---|---|
|**RSA (PKCS#1 v1.5/OAEP)**|Asymmetric|Deterministic, fast, supports digital signatures and key transport. Vulnerable if not properly padded.|
|**Diffie-Hellman (DH)**|Asymmetric|Secure shared secret exchange over insecure channel. Original DH lacks authentication and is vulnerable to MITM.|
|**Elliptic Curve Diffie-Hellman (ECDHE)**|Asymmetric|Modern DH variant with stronger security at shorter key lengths. Enables Perfect Forward Secrecy.|
|**Pre-Shared Keys (PSK)**|Symmetric|Used in environments lacking PKI (e.g., IPsec IKEv1). Simpler but less scalable and prone to shared secret reuse.|

---

### Message Authentication and Integrity

To ensure messages have not been altered in transit and are from a verified sender, **message integrity checks** are embedded into the protocol stack.

#### Methods:

1. **HMAC (Hash-Based Message Authentication Code)**
    
    - Combines a cryptographic hash (e.g., SHA-256) with the session key.
        
    - Construct: `HMAC = H(K ⊕ opad || H(K ⊕ ipad || message))`
        
    - Ensures both integrity and origin authentication.
        
    - Used in TLS 1.2 and earlier, IPsec ESP.
        
2. **Authenticated Encryption with Associated Data (AEAD)**
    
    - Modern encryption modes like AES-GCM or ChaCha20-Poly1305.
        
    - Combines encryption and integrity into one pass.
        
    - Eliminates timing attacks and padding oracle vulnerabilities.
        
    - Mandatory in TLS 1.3.
        
![[ChatGPT Image May 13, 2025, 03_25_01 AM.png]]

---

### Key Terms

- **Session Key:** A randomly generated key used only for the duration of one session. Provides bulk encryption of traffic using symmetric algorithms.
    
- **Digital Envelope:** The symmetric session key is encrypted with a recipient’s public key and delivered alongside the encrypted message.
    
- **Certificate Authority (CA):** A trusted third party that signs digital certificates, binding a public key to an entity’s identity.
    
- **Perfect Forward Secrecy (PFS):** Ensures that compromise of long-term keys (e.g., private keys) does not compromise past session keys.
    

---

### Example Breakdown: TLS with RSA (Deprecated)

```
1. ClientHello — proposes cipher suites, TLS version. 
2. ServerHello — selects suite, sends its certificate with RSA public key. 
3. Client — generates a 256-bit AES session key. 
4. Client — encrypts the session key with server’s RSA public key. 
5. Server — decrypts the session key using its private key. 
6. Both parties — switch to symmetric AES encryption. 
7. Optionally — HMAC is applied for message integrity.`
```

---

### Example Breakdown: TLS 1.3 with ECDHE + AEAD


```
1. ClientHello — includes ECDHE public key. 
2. ServerHello — returns its ECDHE key and certificate. 
3. Both sides — compute the same shared secret (ECDHE). 
4. Key Derivation Function (KDF) — derives AEAD keys. 
5. Encryption — AES-GCM or ChaCha20 used for all application data. 
6. Integrity — provided by AEAD mode (no separate HMAC needed).`
```

---

### Implementation Concerns

- **Key Management:** Security is only as strong as the private key protection. Use HSMs or secure enclaves (e.g., TPM, SGX) for key storage.
    
- **Certificate Validation:** Failure to validate certificates (e.g., accepting self-signed or expired certs) opens systems to MITM attacks.
    
- **Protocol Downgrade Attacks:** Disable legacy protocols (SSLv3, TLS 1.0/1.1) to prevent downgrade exploitation (e.g., POODLE, DROWN).
    
- **Session Hijacking:** Even with encryption, if session IDs are leaked (e.g., via cookies), sessions can be hijacked. Use secure flags, short lifetimes, and rekeying.
    

---

### Summary

| Concept                           | Description                                                        |
| --------------------------------- | ------------------------------------------------------------------ |
| **Data in Motion**                | Data actively moving through network infrastructure.               |
| **Encryption at Transport Layer** | Achieved through TLS, IPsec, WPA, SSH.                             |
| **Key Exchange**                  | RSA (legacy), ECDHE (modern), ensures secure symmetric key setup.  |
| **Symmetric Algorithms**          | AES-GCM, ChaCha20 — used for payload encryption.                   |
| **Integrity Verification**        | HMACs, AEAD modes — ensures authenticity and message validity.     |
| **Forward Secrecy**               | Prevents key compromise from exposing past sessions.               |
| **Implementation Risks**          | Improper cert validation, weak cipher suites, protocol downgrades. |
