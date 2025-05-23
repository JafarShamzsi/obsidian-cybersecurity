## Overview

Network infrastructure can be best understood by analyzing it through the **OSI (Open Systems Interconnection) model**, which defines a layered approach to networking functions. This model enables cybersecurity professionals to pinpoint security responsibilities, assess threats, and enforce layered defenses across a system.

The **OSI model** is composed of 7 layers:

1. **Physical (Layer 1)**
2. **Data Link (Layer 2)**
3. **Network (Layer 3)**
4. **Transport (Layer 4)**
5. **Session (Layer 5)**
6. **Presentation (Layer 6)**
7. **Application (Layer 7)**

![[image-64c9468e08440.jpg]]

---

## Layer 1: Physical

- **Function**: Transmission of raw bits over a physical medium.
- **Media Examples**:
  - Twisted-pair cables (electrical signals)
  - Fiber optics (infrared light)
  - Wireless (radio frequency)
- **Security Focus**:
  - Physical access control (e.g., server room locks, cable management)
  - Electromagnetic interference protection
  - Shielding against physical tapping (TEMPEST compliance)

---

## Layer 2: Data Link

- **Function**: Handles node-to-node communication within the same local segment.
- **Appliances**:
  - **Switches**: Forward frames using **MAC addresses**.
  - **Access Points (APs)**: Bridge wireless hosts with wired networks.
- **Addressing**:
  - **MAC Address**: 48-bit hardware address (e.g., `00-15-5D-01-CA-4A`)
- **Standards**: Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11)
- **Other Concepts**:
  - **VLAN ID**: Logical segmentation (e.g., VLAN 100)
  - **Broadcast Domain**: Scope in which broadcasts are received
- **Security Considerations**:
  - MAC spoofing
  - Port security (e.g., limiting MACs per port)
  - VLAN hopping attacks

---

## Layer 3: Network

- **Function**: Inter-networking, path selection, and logical addressing
- **Appliances**:
  - **Routers**: Forward **IP packets** based on destination IP address
- **Addressing**:
  - **IP Address**: (e.g., `10.1.0.192`)
  - **Subnet**: (e.g., `10.1.0.0/24`)
- **Protocols**:
  - **IP (Internet Protocol)**: Core protocol for routing
  - **ARP (Address Resolution Protocol)**: Resolves IP ↔ MAC (bridges Layer 3 ↔ 2)
- **Security Considerations**:
  - IP spoofing
  - ARP poisoning
  - Route hijacking
  - Firewalls (perimeter defense)

---

## Layer 4: Transport

- **Function**: End-to-end communication, flow control, error checking
- **Protocols**:
  - **TCP (Transmission Control Protocol)**: Reliable, connection-oriented
  - **UDP (User Datagram Protocol)**: Unreliable, connectionless
- **Port Numbers**: Identify specific services (e.g., TCP 80 = HTTP, TCP 443 = HTTPS)
- **Security Considerations**:
  - Port scanning
  - TCP session hijacking
  - SYN flood (DoS attack vector)

---

## Layer 5-6: Session & Presentation (Often Abstracted)

- **Function**:
  - Session: Manages dialogs and sessions between endpoints.
  - Presentation: Data translation, encryption, and compression.
- **Security Role**:
  - TLS (Transport Layer Security) operates across these layers
  - Encryption/decryption
  - Session management and timeout enforcement

---

## Layer 7: Application

- **Function**: Interfaces with the user and provides application-level services
- **Examples**:
  - **HTTP/HTTPS** (Web)
  - **SMTP** (Email)
  - **FTP** (File Transfer)
  - **SMB** (Network shares)
  - **DNS** (Name resolution)
- **Addressing**:
  - **FQDN** (e.g., `www.515support.com`)
- **Infrastructure Service Example**:
  - **DNS**: Although technically an application-layer protocol, it's considered an infrastructure service (critical for resolution of domain names).
- **Security Considerations**:
  - Input validation (prevent injection)
  - Application firewalls (WAF)
  - Protocol abuse (e.g., DNS tunneling)
  - Certificate validation

---

## Key Infrastructure Devices and Functions

| Device         | OSI Layer | Function                                       |
|----------------|-----------|------------------------------------------------|
| Switch         | Layer 2   | Forwards frames using MAC address              |
| Access Point   | Layer 2   | Bridges wireless clients to wired network      |
| Router         | Layer 3   | Forwards packets based on IP address           |
| DNS Server     | Layer 7   | Resolves domain names to IP addresses          |
| Application Server | Layer 7 | Provides services to clients (e.g., HTTP)    |

---

## Cybersecurity Implications Across the Stack

- **Layered Defense (Defense in Depth)**:
  - Physical security → access control
  - Network segmentation → VLANs, firewalls
  - Transport encryption → TLS, VPN
  - Application hardening → input validation, WAF

- **Common Attacks by Layer**:
  - L2: MAC flooding, ARP spoofing
  - L3: IP spoofing, route injection
  - L4: Port scanning, DoS
  - L7: Injection attacks, protocol abuse

- **Security Best Practices**:
  - Enforce **network segmentation** to limit lateral movement
  - Use **strong encryption** at transport and application layers
  - Monitor and **log traffic** at each layer using IDS/IPS
  - Implement **access control lists (ACLs)** and **role-based access**