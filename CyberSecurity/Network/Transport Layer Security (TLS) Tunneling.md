Transport Layer Security (TLS) tunneling is a secure method for implementing **remote access VPNs**. It provides **confidentiality**, **authentication**, and **integrity** for network traffic by encapsulating it within an encrypted TLS session.

A TLS VPN typically uses protocols such as **OpenVPN**, which operate at **Layer 4 (transport)** or above and can tunnel traffic securely through restrictive firewalls and NAT devices.

---

## TLS VPN Operation

### 1. **Initial Connection**
- The **client connects to the VPN gateway** using a public IP address and port (e.g., UDP/1194).
- The VPN server presents its **digital certificate** to the client. This certificate is:
  - Signed by a trusted **Certificate Authority (CA)**
  - Used to verify the **identity of the server**

### 2. **Mutual Authentication (Optional)**
- The client may also present a certificate to the server.
- This enables **mutual TLS (mTLS)** — both parties verify each other’s identity.
- This is often enforced by **TLS certificate depth settings**.

### 3. **Authentication and Tunnel Establishment**
- Once TLS is negotiated:
  - The user submits **credentials** (e.g., username/password) through the encrypted tunnel.
  - These are typically verified via **RADIUS or LDAP authentication**.
- Upon successful authentication:
  - A secure **VPN tunnel** is established
  - All internal network communications are routed through this TLS-encrypted channel
![[7460-1692974865786.png]]
---

## Example: OpenVPN + OPNsense

### General Configuration
- **Server Mode**: Remote Access (SSL/TLS + User Auth)
- **Backend for Authentication**: RADIUS server (e.g., Structureality)
- **Protocol**: UDP (often preferred over TCP for performance)
- **Device Mode**: tun (routed IP tunnel)
- **Port**: 1194 (default for OpenVPN)

### Cryptographic Settings
- **TLS Authentication**: Enabled
  - Uses a pre-shared key for extra control-plane protection
- **Peer Certificate Authority**: Custom CA (e.g., Structureality Enterprise Root)
- **Server Certificate**: VPN server’s identity cert
- **Auth Digest Algorithm**: SHA-256
- **Certificate Depth**: 1 (client + server)
- **Strict CN Matching**: Optional (for verifying subject names)

---
![[8581-1692974865849.png]]
## TLS Protocol Versions

### Recommended:
- **TLS 1.3** – Most secure, faster handshake, forward secrecy by default
- **TLS 1.2** – Still secure and widely supported

### Deprecated:
- **TLS 1.0 & 1.1**
  - Vulnerable to downgrade attacks, weak cipher suites
  - **Must not be used**

---

## TCP vs UDP for TLS VPNs

| Protocol | Use Case | Notes |
|----------|----------|-------|
| **UDP**  | Default for OpenVPN | Better performance for voice/video, no retransmission overhead |
| **TCP**  | Firewall-friendly   | More compatible with deep packet inspection, easier NAT traversal |
| **DTLS** | TLS over UDP        | Used for latency-sensitive apps; OpenVPN does not use DTLS per se, but similar effect via UDP |

---

## Security Considerations

- **Use a trusted CA hierarchy** to issue and manage certificates
- **Enforce strong TLS configurations** (disable older versions, weak ciphers)
- **Enable MFA** on top of certificate-based auth for defense-in-depth
- **Monitor VPN logs** for signs of brute-force or certificate misuse
- Use **certificate revocation lists (CRLs)** or OCSP to manage compromised credentials

---

## Related Concepts

- [[TLS vs IPsec VPNs]]
- [[OpenVPN Configuration Best Practices]]
- [[RADIUS Authentication Protocol]]
- [[Mutual TLS (mTLS)]]
- [[TLS Certificate Management]]
- [[Datagram Transport Layer Security (DTLS)]]
