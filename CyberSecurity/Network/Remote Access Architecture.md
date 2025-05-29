Remote access networking refers to any method by which a user connects to an internal network infrastructure without a direct local (wired or wireless) link. Instead, the user connects through an **intermediate untrusted network**, most commonly the public internet.

---

## Remote Access Use Case

Remote access solutions are essential for:

- **Telecommuting employees**
- **Traveling staff**
- **Field technicians**
- **Third-party contractors or vendors**

The primary security concern is **protecting data in transit** across insecure networks.

---
![[image-5fab20d6c544b.jpg]]
## Remote Access Topologies

### 1. Remote Access VPN (Client-to-Site)

- The **user device (client)** connects to a **VPN gateway** on the corporate network perimeter.
- A **secure encrypted tunnel** is established to encapsulate traffic.
- Enables users to:
  - Access internal file servers
  - Use corporate applications
  - Perform management or administrative tasks remotely

#### Characteristics:
- Tunnel initiated by the **client device**
- Traffic is encrypted using **IPsec** or **TLS/SSL**
- Often requires **user authentication** (MFA recommended)
- Network access is governed by **access control policies**

---

### 2. Site-to-Site VPN

- Connects **two or more entire networks** securely across a public or third-party network.
- Typically used for:
  - Branch office integration
  - Multi-datacenter connections

#### Characteristics:
- VPN tunnels established between **VPN gateways**
- Operates automatically once configured
- Hosts are unaware of the VPN; routing rules handle traffic forwarding
- IPsec is the dominant protocol for these deployments
- Strong mutual authentication between gateways using certificates or pre-shared keys (PSKs)

---

### 3. Host-to-Host VPN

- Establishes a **secure tunnel between two individual systems**
- Used when:
  - Two computers must exchange sensitive data over an untrusted network
  - There is no need or ability to tunnel entire networks

#### Characteristics:
- VPN tunnel directly between host devices
- Often used for **server-to-server replication**, secure remote shell (SSH) tunneling, or secure application-layer tunnels
- IPsec Transport Mode is often used instead of Tunnel Mode

---

## VPN Protocols

### Deprecated Protocols

- **PPTP (Point-to-Point Tunneling Protocol)**
  - Weak encryption (MS-CHAPv2), vulnerable to brute-force attacks
  - No longer considered secure; **should not be used**

### Secure Protocols

#### 1. IPsec (Internet Protocol Security)
- **Layer 3 protocol** that provides secure tunneling
- Supports:
  - Encryption (ESP)
  - Authentication (AH)
  - Key exchange (IKEv2)
- Can operate in:
  - Tunnel mode (entire packet is encrypted)
  - Transport mode (payload encrypted, header intact)

#### 2. TLS/SSL
- **Layer 4/Layer 7 protocol**, commonly used for remote access VPNs
- Secure Web VPNs: use TLS to allow VPN access through standard web browsers
- Easier NAT traversal and firewall compatibility than IPsec

#### 3. OpenVPN
- Open-source VPN solution
- Uses TLS/SSL for key negotiation and secure communication
- Highly configurable and widely used in both enterprise and small-scale deployments
![[image-5fabec2a7885d.jpg]]
---

## Security Considerations

- **Authentication**:
  - Username/password + MFA (e.g., token, app, certificate)
- **Access Control**:
  - Define granular policies (who can access what, from where, and when)
- **Monitoring and Logging**:
  - Ensure all remote sessions are audited
  - Look for signs of compromise or unusual activity
- **Split Tunneling**:
  - Allows users to access local and remote networks simultaneously
  - Increases risk of man-in-the-middle attacks or data exfiltration

---

## Related Concepts

- [[Virtual Private Network (VPN)]]
- [[IPsec vs SSL VPNs]]
- [[Network Access Control (NAC)]]
- [[Firewall and Gateway Configuration]]
- [[Zero Trust Network Access (ZTNA)]]
