**Internet Key Exchange (IKE)** is the protocol used to establish **Security Associations (SAs)** in IPsec. These SAs define how two peers (hosts or gateways) will **authenticate**, **negotiate cryptographic parameters**, and **exchange keys** securely. IKE provides the control channel for negotiating encryption and integrity policies for AH/ESP and supports both **transport** and **tunnel** mode.

---

## Security Association (SA)

A **Security Association** is a unidirectional agreement between two peers on the following:
- Authentication method (e.g., RSA certs or PSK)
- Cryptographic suite (encryption + integrity)
- Key exchange parameters
- Lifetime and rekeying policy
- Mode: AH or ESP, and transport vs tunnel

---

## IKE Phases

### Phase I: Secure Channel Establishment
- Authenticates peers and establishes a secure, encrypted control channel using the **Diffie-Hellman** (DH) algorithm
- Negotiates cryptographic parameters
- Authenticates using:
  - **Pre-shared key (PSK)**
  - **Digital certificates (RSA, ECC)**
- Results in an **IKE SA**

#### Example Configuration (OPNsense):

### Phase 1:

- Auth Method: Mutual RSA
    
- My ID: IP address
    
- Peer ID: IP address
    
- My Certificate: structureality site-to-site VPN
    
- CA: structureality enterprise root
    

### Phase 1 Algorithms:

- Encryption: AES-GCM 256-bit (ICV 128-bit)
    
- Integrity: SHA-256
    
- DH Group: 14 (2048-bit)


### Phase II: IPsec Tunnel Negotiation
- Uses secure channel from Phase I to negotiate:
  - AH or ESP use
  - Encryption and hashing algorithms
  - Key length and lifetime
- Establishes **IPsec SA** for protecting actual data traffic
![[3784-1692974866208.png]]
---

## IKE Authentication Methods

### 1. **Pre-shared Key (PSK)**
- Same passphrase configured on both peers
- Simpler but less scalable and less secure for large environments
- Vulnerable to brute-force and dictionary attacks if weak keys are used

### 2. **Digital Certificates**
- X.509 certificates issued by a trusted Certificate Authority (CA)
- Offers strong, scalable authentication
- Common in enterprise and remote access deployments

---

## IKE Versions

### IKEv1
- Traditional two-phase approach
- Requires additional protocols (e.g., L2TP) for remote access
- Lacks NAT traversal support by default

### IKEv2 (RFC 7296)
- More efficient and robust than IKEv1
- Reduces message exchange (fewer round-trips)
- Improved resilience and security features

#### Key Enhancements in IKEv2:
- **EAP Support**: Enables integration with RADIUS and Active Directory for user authentication
- **NAT Traversal**: Encapsulates traffic in UDP to traverse NAT devices
- **MOBIKE Support**: Allows IPsec connection persistence across multiple interfaces (e.g., Wi-Fi ↔ LTE)
- **Simpler Configuration**: Fewer configuration errors, better defaults
- **DoS Protection**: Stateless cookies protect against resource exhaustion

---

## Cryptographic Negotiation Parameters

- **Encryption**: AES (128/192/256), AES-GCM
- **Integrity**: SHA-1, SHA-256, SHA-384
- **DH Groups**:
  - Group 14: 2048-bit MODP (safe baseline)
  - Group 19: 256-bit ECDH (better performance and security)
  - Group 20: 384-bit ECDH (strong security)

> ✅ Use **AES-GCM** with strong DH groups (≥ Group 14) for modern deployments.

---

## Use Case: Site-to-Site VPN with RSA Certs (OPNsense)

- **Phase 1** authenticates peers using X.509 certs
- **Phase 2** negotiates ESP tunnel with AES-GCM and SHA-256
- Allows secure routing between:
  - Local network: LAN subnet (e.g., 192.168.1.0/24)
  - Remote network: e.g., 10.2.48.0/24
- Common for **branch office connectivity**, **enterprise WAN security**

---

## Related Topics

- [[IPsec Tunneling]]
- [[ESP vs AH]]
- [[Diffie-Hellman Key Exchange]]
- [[IKEv2 MOBIKE and NAT-T]]
- [[X.509 Certificates in VPN]]
