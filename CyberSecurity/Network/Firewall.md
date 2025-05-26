
A **firewall** is a preventive security control used to enforce policy on traffic entering and exiting a network segment. Firewalls operate by inspecting network packets and applying rule-based logic to allow or deny traffic, making them foundational to network perimeter defense and internal segmentation.

---

## Packet Filtering

Packet filtering is a core firewall function. Firewalls operate using rule sets, commonly implemented as **Access Control Lists (ACLs)**. These rules examine Layer 3 (IP) and Layer 4 (Transport) headers to determine whether a packet should be allowed or denied. Filtering types include:

### IP Filtering
- Filters traffic based on source or destination **IP addresses**.
- May be extended to MAC address filtering on some devices.

### Protocol Filtering
- Filters based on the **IP protocol field** (e.g., TCP, UDP, ICMP).
- Common use cases: blocking ICMP ping requests, restricting GRE tunneling.

### Port Filtering
- Filters packets based on **source/destination TCP or UDP port numbers**.
- Enables service-level control (e.g., block outbound SMTP on port 25).

### Rule Actions
- **Accept / Permit** – Allows packet through.
- **Drop / Deny** – Silently discards the packet with no response.
- **Reject** – Discards packet and sends an ICMP notification (e.g., Port Unreachable).

Inbound and outbound traffic can be managed separately. Outbound filtering is useful for:
- Preventing unauthorized applications from communicating.
- Detecting or stopping malware (e.g., backdoor communication, C2 traffic).

---

## Firewall Deployment Modes

Firewalls can be implemented in hardware, as virtual appliances, or as host-based software. Deployment mode significantly influences the firewall's role and performance.

### Routed Mode (Layer 3 Firewall)
- Each interface is tied to a unique IP subnet.
- Performs packet forwarding/routing between zones.
- Interfaces possess both IP and MAC addresses.
- Commonly used at perimeter and inter-VLAN points.

### Bridged Mode (Layer 2 Firewall)
- Operates like a transparent Ethernet bridge.
- Inspects traffic at Layer 2 while analyzing Layer 3/4 headers.
- Interfaces have MAC addresses, but not IPs.
- Avoids the need to reassign IPs or alter subnets.
- Suitable for insertion between router and switch or in front of servers.

### Inline Mode (Layer 1 / Virtual Wire)
- Firewall acts as a transparent bump-in-the-wire.
- Interfaces do not have MAC or IP addresses.
- Traffic is either allowed or blocked with no routing or switching.
- Offers stealth insertion without changes to existing infrastructure.
- Must consider fail-open vs fail-closed behavior.

---

## Transparent Firewalls

Bridged and inline modes are collectively known as **transparent mode** firewalls. These are designed for integration into networks without IP reconfiguration or topology changes.

- Management requires a **dedicated interface** with an IP address.
- Transparent firewalls can be used for inline threat detection, web server protection, or enforcing policy between segments.

Management interfaces can be:
- **Dedicated**: More secure, avoids exposure to normal traffic paths.
- **Shared**: Less secure, allows management traffic over existing interfaces (more common in routed mode).

---

## Router Firewalls

**Router firewall appliances** integrate filtering capabilities directly into router firmware. While primarily designed for routing, these devices can perform:

- Stateful packet inspection
- NAT and port forwarding
- Basic application filtering

Typical of Small Office/Home Office (SOHO) routers:
- Often include pre-defined rule sets for ease of use.
- May lack flexibility and depth compared to enterprise-grade firewalls.

---

## Monitoring Example: OPNsense

**OPNsense** is an open-source firewall platform. Its web-based dashboard provides key operational metrics:

- **System Information**: Hostname, OS version, CPU usage, uptime, last config change.
- **Services Panel**: List of running daemons and their status.
- **Gateways Panel**: Monitors round-trip time (RTT), packet loss, and connectivity.
- **Interfaces Panel**: Shows live bandwidth usage per interface.
- **Traffic Graph**: Visual representation of real-time traffic patterns.

Use cases for OPNsense include:
- Network segmentation
- VPN termination
- Transparent filtering
- Home lab security

---

## Comparison Table: Deployment Modes

| Attribute               | Routed Mode (L3)     | Bridged Mode (L2)    | Inline Mode (L1)        |
|------------------------|----------------------|-----------------------|--------------------------|
| OSI Layer              | Layer 3              | Layer 2               | Layer 1                 |
| IP Address Required    | Yes                  | No (Mgmt only)        | No                      |
| MAC Address            | Yes                  | Yes                   | No                      |
| Re-IP Required         | Yes                  | No                    | No                      |
| Typical Use Case       | Perimeter firewall   | Transparent filtering | High-stealth enforcement |

---

## Security Considerations

- **Fail-Safe Behavior**: Inline devices must define fail-open vs. fail-closed in case of power loss.
- **Logging and Auditing**: Log firewall events and forward to a SIEM or log management platform.
- **Management Interface Hardening**: Restrict management access to trusted networks; use VLAN isolation or out-of-band management.
- **Rule Complexity**: Simpler rules reduce misconfiguration risk. Use hierarchical or role-based rulesets.
- **Testing and Simulation**: Validate new rules in test environments before deploying.

---

## Related Topics

- [[Intrusion Detection and Prevention Systems]]
- [[Network Segmentation and DMZ]]
- [[Security Zones and VLAN Design]]
- [[NAT and PAT Mechanisms]]
- [[Zero Trust Architecture]]

