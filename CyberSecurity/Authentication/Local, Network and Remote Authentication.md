## Introduction

Authentication is a fundamental security control in all modern operating systems. It involves verifying a user's identity prior to granting access to system resources, services, or shells. Authentication mechanisms are broadly categorized into:

- Local Authentication
- Network-based Authentication
- Remote Authentication

Each model depends on credential types, trust boundaries, and the architecture of the underlying authentication provider.

---

## Knowledge-Based Authentication (KBA)

Knowledge-based authentication typically relies on the secrecy of a shared credential, most commonly a password.

### Password Hashing

Instead of storing passwords in plaintext, systems hash passwords using one-way cryptographic algorithms. Upon login:

1. The user inputs a password.
2. The system hashes the input using a predefined hash function (e.g., SHA-512, bcrypt, PBKDF2).
3. The resulting hash is compared to the stored hash.
4. If the hashes match, authentication is successful.

This model mitigates the risk of credential disclosure through static file compromise, assuming the hash function and salting mechanism are strong.

---

## Windows Authentication Architecture

Windows authentication is implemented through a set of tightly integrated components. Primary among these is the **Local Security Authority Subsystem Service (LSASS)**, which manages authentication and enforces security policies.

### Local Sign-in (Interactive Logon)

- LSASS compares the provided credentials against hashes stored in the **Security Accounts Manager (SAM)** database.
- SAM is located in the Windows Registry (`HKLM\SAM`) and is ACL-restricted.
- Credentials are stored as **NT Hashes** (historically LM Hashes as well, which should be disabled).

### Network Sign-in (Domain Authentication)

- Occurs in Active Directory (AD) environments.
- LSASS forwards authentication to a **Domain Controller (DC)**.
- The default authentication protocol is **Kerberos v5**, with fallback to **NT LAN Manager (NTLMv2)** for legacy systems.

#### Kerberos Authentication

- Based on a **ticket-granting** model.
- Involves:
  - Authentication Service (AS) Exchange
  - Ticket-Granting Service (TGS) Exchange
  - Client/Server (AP) Exchange
- Uses symmetric cryptography with **Key Distribution Center (KDC)** consisting of AS and TGS.

#### NTLM Authentication

- Challenge-response protocol.
- Client generates an HMAC-MD4 hash of the password.
- Susceptible to:
  - Pass-the-hash (PtH)
  - Relay attacks
  - Offline brute force if hashes are compromised

### Remote Sign-in (Off-Network Access)

- Utilized when the client is external to the domain's LAN.
- Access may be routed through:
  - VPN using IPSec or SSL
  - 802.1X authenticated enterprise Wi-Fi with RADIUS backend
  - Web portals using federated SSO (e.g., SAML, OpenID Connect)

- Protocols such as **EAP-TLS**, **PEAP**, or **RADIUS** are used to provide secure channel-based mutual authentication.

---

## Linux Authentication Architecture

Linux authentication mechanisms are modular and extensible, often built around simple text file databases and pluggable modules.

### Local Authentication

- User account metadata resides in `/etc/passwd`.
- Password hashes reside in `/etc/shadow`.
- File is only accessible by root or processes with elevated privileges.

Hashing mechanisms typically used include:

- SHA-512 (`$6$`)
- bcrypt (`$2b$`)
- scrypt or Argon2 via PAM modules

### Remote Authentication (SSH)

- Secure Shell (SSH) is used for encrypted remote logins.
- Authentication methods:
  - Password-based
  - Public Key-based
  - Certificate-based (via OpenSSH CA or third-party CAs)

SSH keys use asymmetric cryptography:

- User holds a private key (e.g., RSA, ECDSA, ED25519)
- Public key is added to `~/.ssh/authorized_keys` on the target host
- Server challenges with a nonce; client signs with the private key; server verifies using public key

### Pluggable Authentication Modules (PAM)

PAM provides a dynamic and flexible mechanism for authenticating users and managing credentials. Each PAM service comprises a stack of modules defined in configuration files under `/etc/pam.d/`.

PAM supports:

- Authentication backends (e.g., LDAP, RADIUS, Kerberos)
- Password complexity and aging policies
- Smart card and biometric modules
- Account and session lifecycle hooks

PAM configuration must be hardened to prevent:

- Credential caching bypass
- Account locking misconfigurations
- Insecure fallback paths

---

## Protocol Comparison Table

| Feature                         | Windows                                   | Linux                                       |
|----------------------------------|--------------------------------------------|----------------------------------------------|
| Local Credential Store          | SAM (Registry-backed DB)                  | /etc/passwd and /etc/shadow                 |
| Default Hashing Algorithm       | NT Hash (MD4, unsalted)                   | SHA-512, bcrypt, scrypt (via PAM)           |
| Remote Auth Protocol            | VPN (EAP, MSCHAPv2), WebAuthn, RADIUS     | SSH (PKI), PAM + Kerberos/LDAP              |
| Directory Service Integration   | Active Directory                          | LDAP, FreeIPA, Kerberos                     |
| Authentication Core Service     | LSASS                                     | PAM                                         |
| Multi-Factor Authentication     | Smart cards, Windows Hello, Azure MFA     | PAM plugins, Google Authenticator, Duo PAM  |
| Vulnerabilities                 | NTLM Relay, Pass-the-Hash, Credential Dump | PAM misconfiguration, key reuse, open SSH   |

---

## Security Considerations and Best Practices

1. **Use strong, salted hashes** for password storage. Avoid MD5, SHA-1, or unsalted NT hashes.
2. **Disable NTLM** and legacy authentication protocols wherever possible.
3. **Enforce multi-factor authentication** (MFA) especially for remote access.
4. **Apply least privilege principles** to authentication services and credential storage.
5. **Audit logs** of LSASS (Windows Event ID 4624/4625) and SSHD (Linux `/var/log/auth.log`) for anomalous behavior.
6. **Implement account lockout policies** and rate limiting to prevent brute force attacks.
7. **Use hardware-backed credential stores** (e.g., TPM, YubiKey) where supported.

---

## References

- Microsoft: [Credentials Processes in Windows Authentication](https://docs.microsoft.com/en-us/windows-server/security/windows-authentication/credentials-processes-in-windows-authentication)
- `man pam`, `man sshd`, `man shadow`
- NIST SP 800-63: Digital Identity Guidelines
- MIT Kerberos Documentation
