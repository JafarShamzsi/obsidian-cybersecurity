**IPsec (Internet Protocol Security)** is a suite of protocols designed to secure IP communications by **authenticating**, **integrity-checking**, and optionally **encrypting** each IP packet. Unlike TLS, which operates at the **application layer (Layer 7)**, IPsec operates at the **network layer (Layer 3)**, enabling transparent protection for any IP-based protocol without requiring application modification.

---

## Core IPsec Protocols

### 1. **Authentication Header (AH)**
- Provides **integrity** and **authentication**, but **not confidentiality**
- Protects both the IP header and the payload
- Uses a **cryptographic hash** + shared secret to generate an **Integrity Check Value (ICV)**
- Ensures the packet has not been **tampered with** in transit

> ❗ AH is often avoided in favor of ESP due to lack of encryption.

---

### 2. **Encapsulating Security Payload (ESP)**
- Provides **encryption (confidentiality)**, **integrity**, and **authentication**
- Encrypts the **payload only** in transport mode or **entire packet** in tunnel mode
- Adds:
  - **ESP Header**
  - **ESP Trailer** (for padding and alignment)
  - **Integrity Check Value (ICV)**

> ✅ ESP is the most commonly used IPsec protocol.

---

## Modes of Operation

### Transport Mode
- Used for **host-to-host** secure communication
- Only the **payload** is encrypted; **original IP header is left intact**
- Common for securing traffic **within a LAN or between trusted hosts**
![[9434-1692974865939.png]]
#### Use Cases:
- Internal communications on private networks
- End-to-end security between client and server

#### With ESP:
- Payload encrypted
- IP header visible (enables routing)

#### With AH:
- Payload and IP header integrity-protected (but not encrypted)

---

### Tunnel Mode
- Used for **gateway-to-gateway (site-to-site)** or **host-to-gateway** VPNs
- **Entire IP packet is encrypted** and encapsulated within a **new IP header**
- Provides full confidentiality across **untrusted networks** like the Internet
![[1132-1692974866005.png]]
#### Use Cases:
- Site-to-site VPNs
- Remote access scenarios with IPsec tunneling

#### ESP in Tunnel Mode:
| New IP Header | ESP Header | Original IP Header + Payload | ESP Trailer | ICV |


---

## Deployment Example: OPNsense + IPsec Site-to-Site VPN

- **Mode**: Tunnel IPv4
- **Description**: Remote office VPN
- **Local Network**: LAN subnet (e.g., 192.168.1.0/24)
- **Remote Network**: 10.2.48.0/24
- **Phase 2 Proposal**: 
  - **Protocol**: ESP
  - **Encryption + Hashing algorithms** negotiated per security policy

> 🔧 This configuration encrypts entire IP packets between two network gateways over the public Internet.
![[3806-1692974866142.png]]
---

## IPsec Configuration and Negotiation

- Security Associations (SAs) are negotiated using:
  - **IKEv1** (legacy)
  - **IKEv2** (preferred for mobility, reliability, and efficiency)
- Uses X.509 certificates or pre-shared keys (PSK) for peer authentication
- Policies define:
  - Protocol (ESP/AH)
  - Encryption algorithm (e.g., AES)
  - Integrity algorithm (e.g., SHA-2)
  - Key lifetime and rekeying intervals

---

## Security Considerations

- **ESP with Tunnel Mode + IKEv2 + AES-GCM** is considered highly secure
- **AH** is rarely used due to lack of confidentiality
- Avoid **DES**, **MD5**, and weak DH groups
- Implement **Perfect Forward Secrecy (PFS)** with strong DH groups (e.g., Group 14, 19, 20)
- Use **certificate-based authentication** instead of PSK for better scalability and security

---

## Comparison: IPsec vs TLS VPN

| Feature                 | IPsec                       | TLS VPN (e.g., OpenVPN)          |
|------------------------|-----------------------------|----------------------------------|
| OSI Layer              | Layer 3 (Network)           | Layer 5/6 (Session/Transport)    |
| Flexibility            | Transparent to applications | App-specific                     |
| NAT Traversal          | Requires workarounds        | NAT-friendly (uses TCP/UDP)      |
| Performance            | Lower overhead              | Slightly more overhead           |
| Deployment Complexity  | Moderate to High            | Low to Moderate                  |

---

## Related Topics

- [[TLS Tunneling]]
- [[IPsec IKEv2 Negotiation]]
- [[Site-to-Site VPN Configuration]]
- [[ESP vs AH]]
- [[Transport Mode vs Tunnel Mode]]
