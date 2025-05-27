Firewalls can operate at different layers of the OSI model, most commonly at Layer 4 (Transport) and Layer 7 (Application). The distinction reflects both the depth of packet inspection and the context-awareness the firewall can apply to traffic analysis.

---

## Stateless vs Stateful Firewalls

### Stateless Firewalls
- Operate purely on **individual packets**, with no context of session or connection state.
- Use **packet filtering rules** (IP, protocol, port) to determine if a packet is permitted.
- Require minimal system resources and are typically faster.
- Vulnerable to attacks that span multiple packets (e.g., session hijacking, TCP fragmentation).
- Struggle with **dynamic port negotiation** (e.g., for FTP, VoIP, or load balancers).
- Example: Simple ACLs on a router.

### Stateful Inspection Firewalls
- Maintain context about **active sessions** in a **state table**.
- Analyze protocols such as **TCP** for valid session establishment (e.g., SYN → SYN/ACK → ACK).
- Once a connection is deemed valid, subsequent packets in the session are allowed with minimal inspection.
- Detects anomalies such as:
  - **Unsolicited SYN packets**
  - **Out-of-order sequence numbers**
  - **IP/ICMP header manipulation**
- More secure and flexible, with moderate performance overhead.
![[3887-1692974864580.png]]
---

## Layer 4 Firewall

A Layer 4 (Transport Layer) firewall uses **stateful inspection** to evaluate and track session-related characteristics.

### Key Capabilities
- Monitors TCP three-way handshake to validate session establishment.
- Uses **sequence and acknowledgment numbers** to detect abnormal flows.
- Can:
  - Drop **SYN floods** (DoS attack)
  - Block **incomplete handshakes**
  - Identify **connection hijacking attempts**
- Tracks **UDP flows** based on source IP, destination IP, source port, and destination port.
  - Since UDP is connectionless, firewalls use timing heuristics to infer state (idle timeout).
- May inspect:
  - **ICMP types and codes**
  - **IP header anomalies** (e.g., spoofing, fragmentation)

### Performance Considerations
- Faster than application-layer firewalls due to limited inspection depth.
- Typically used at **network perimeters**, **DMZ**, or **VPN concentrators**.

### Example: OPNsense State Table
- Tracks all active sessions with:
  - Source/Destination IP and Port
  - Protocol
  - Session start and expiration time
- Can be configured to:
  - Limit max states per IP
  - Use adaptive timeouts
  - Enforce global state table limits

---

## Layer 7 Firewall

A Layer 7 (Application Layer) firewall inspects **application-level protocols and data**, offering deeper visibility and control over traffic behavior.

### Capabilities
- Performs **deep packet inspection (DPI)** of both headers and payloads.
- Recognizes and validates **application-layer protocols** (e.g., HTTP, FTP, SMTP).
- **Application awareness**:
  - Can detect applications **disguised** as legitimate traffic on common ports.
  - E.g., block non-HTTP traffic sent over TCP port 80.
- Detects **protocol violations**, **injected commands**, and **malicious payload patterns**.

### Use Cases
- **Web Application Firewalls (WAFs)**:
  - Analyze HTTP/S traffic
  - Inspect headers, cookies, request bodies
  - Block SQLi, XSS, CSRF patterns
- **Mail Gateways**:
  - Enforce content policies on SMTP, IMAP, POP3
  - Detect phishing, malware attachments
- **NGFW (Next-Generation Firewalls)**:
  - Combine traditional L4 filtering with L7 inspection
  - Integrate threat intelligence feeds and behavioral heuristics

### Alternate Names
- Application Layer Gateway (ALG)
- Stateful Multilayer Inspection
- Deep Packet Inspection (DPI)

### Limitations
- **Resource-intensive**: DPI increases CPU and memory usage.
- **Encrypted traffic** (e.g., HTTPS, TLS) requires decryption for full inspection:
  - Often implemented via **SSL/TLS inspection** (requires man-in-the-middle proxy).
  - Introduces **privacy**, **latency**, and **certificate management** concerns.
- Protocol parsing must be frequently updated to avoid evasion.

---
![[7303-1692974864649.png]]
## Security Considerations

- **Evasion Techniques**:
  - Tunneling protocols within allowed ports (e.g., SSH over HTTPS)
  - Fragmentation attacks to bypass pattern detection
  - Obfuscation using encoding (Base64, Unicode)

- **Best Practices**:
  - Use Layer 7 inspection at network egress points and for high-risk services.
  - Deploy Layer 4 firewalls at perimeter or internal segmentation points for performance efficiency.
  - Enforce SSL inspection policies carefully, with exceptions for sensitive services.
  - Apply **least privilege rules**: allow only known, expected, and validated protocols on required ports.

---

## Summary Comparison

| Feature                       | Layer 4 Firewall            | Layer 7 Firewall                   |
|------------------------------|-----------------------------|------------------------------------|
| OSI Layer                    | Transport (Layer 4)         | Application (Layer 7)              |
| Inspection Depth             | Headers only                | Headers + Payload (DPI)            |
| State Tracking               | TCP/UDP stateful            | Application session awareness      |
| Protocol Awareness           | IP, TCP/UDP, ICMP           | HTTP, FTP, SMTP, DNS, etc.         |
| Performance                  | Higher                      | Lower (heavier processing)         |
| Application Verification     | No                          | Yes                                |
| Encrypted Traffic Handling   | Limited                     | Requires SSL inspection            |
| Attack Detection Capability  | Limited to DoS, port scans  | Detects injection, evasion, exfil. |

---

## Related Notes

- [[Firewalls]]
- [[Deep Packet Inspection]]
- [[Web Application Firewalls (WAF)]]
- [[Intrusion Prevention Systems (IPS)]]
- [[Next-Generation Firewalls (NGFW)]]
