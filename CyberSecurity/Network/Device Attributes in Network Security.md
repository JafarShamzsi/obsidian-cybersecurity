## Overview
Device attributes define how a security device is integrated into a network, how it processes traffic, and how it behaves under failure conditions. Understanding these attributes is essential for designing secure and resilient network architectures.

---

## 1. Active vs. Passive Security Controls

### Active Controls

**Definition**: Active controls interact directly with endpoints or network traffic and typically require configuration, authentication, or agent software.

**Examples**:
- **Vulnerability Scanners**: Require credentials and direct access to the target host.
- **Firewalls**: Require routing changes and host reconfiguration to route traffic through them.
- **Antivirus Agents**: Installed on hosts and actively analyze behavior or file signatures.

**Characteristics**:
- Requires endpoint integration.
- May introduce latency.
- Detects and mitigates threats in real time.
- May be detected or disrupted by adversaries.

**Risks**:
- Credential leakage.
- Incorrect configuration may disrupt normal operations.
- Attack surface increases due to direct interaction.

---
![[9719-1692974864420.png]]
### Passive Controls

**Definition**: Passive controls monitor and analyze traffic or system behavior without altering it or requiring interaction with the endpoint.

**Examples**:
- **Network TAPs**: Physical layer devices that mirror traffic.
- **SPAN/Mirror Ports**: Configured on switches to copy traffic to analyzers.
- **IDS (Intrusion Detection System)**: Listens passively for malicious patterns.

**Characteristics**:
- No endpoint configuration needed.
- Transparent to hosts.
- Cannot block or alter traffic.
- Often used for alerting and forensic analysis.

**Risks**:
- Blind to encrypted traffic unless decryption is available.
- Cannot stop an attack—only detect.

---

## 2. Inline Devices vs. Monitor Methods

### Inline Devices

**Definition**: Devices physically placed in the path of network traffic.

**Attributes**:
- Receive and forward live traffic.
- Often lack IP or MAC addressing.
- Can enforce policies (e.g., IPS, firewall).

**Examples**:
- **IPS (Intrusion Prevention System)**.
- **Next-Gen Firewalls**.
- **Inline TAPs**.

**Pros**:
- Immediate mitigation capabilities.
- Effective for real-time enforcement.

**Cons**:
- Potential single point of failure.
- Requires robust failover mechanisms.

---

### Monitor Methods

#### 1. Test Access Point (TAP)

**Definition**: Hardware device that physically duplicates network signals.

**Details**:
- Operates at Layer 1 (physical).
- Copies all traffic (including errors or malformed frames).
- Transparent to endpoints.

**Usage**:
- Ideal for packet capture and deep analysis.
- Immune to load-related drops.

**Risks**:
- Physical tampering can disrupt flow.
- Requires physical access to deploy or modify.

#### 2. SPAN/Mirror Port

**Definition**: Logical duplication of traffic by a switch.

**Details**:
- Configured at Layer 2.
- Can be selective (port-based or VLAN-based).
- Traffic copied to an analyzer port.

**Limitations**:
- Dropped frames under high load.
- Does not capture corrupt or errored frames.
- Can be misconfigured or disabled remotely.

**Security Notes**:
- Should be protected against reconfiguration attacks.
- Should not be relied on for complete forensic accuracy.

---

## 3. Fail-Open vs. Fail-Closed

### Failure Scenarios

- **Hardware Failures**: Overheating, PSU failure, physical damage.
- **Software Issues**: Kernel panics, crashes, memory leaks.
- **Configuration Errors**: Syntax errors, misapplied policies, lack of redundancy.
- **External Events**: Natural disasters, power outages, DoS attacks.

---

### Fail-Open

**Definition**: System defaults to allowing access when failure occurs.

**Attributes**:
- Prioritizes availability.
- Common in high-availability environments (e.g., emergency services, healthcare).
- Often implemented via hardware bypass or relay-based TAPs.

**Risks**:
- Attackers may induce failure to bypass controls.
- Exposure of sensitive systems during outages.

**Example**:
- Firewall fails open to avoid service disruption.

---

### Fail-Closed

**Definition**: System blocks access or shuts down during failure.

**Attributes**:
- Prioritizes security over availability.
- Common in financial, government, and classified environments.
- May introduce downtime or service loss.

**Risks**:
- Critical services may become inaccessible.
- May trigger cascading failures if dependencies are not well managed.

**Example**:
- Inline IPS drops all traffic if it crashes.

---

## 4. Design Considerations

| Attribute          | Active                  | Passive                  |
|-------------------|-------------------------|--------------------------|
| Endpoint Integration | Required              | Not Required             |
| Visibility         | High (interactive)      | Medium (observational)   |
| Impact Potential   | High                    | Low                      |
| Risk               | Higher (visible target) | Lower (stealthy)         |

| Attribute         | Inline Device           | Monitor Method (TAP/SPAN) |
|------------------|--------------------------|----------------------------|
| Traffic Flow      | Intercepted/modified     | Observed only              |
| Risk of Interruption | High (Single point)   | Low (Mirror-only)          |
| Failover Support  | Critical                 | Optional                   |

| Fail Mode         | Fail-Open               | Fail-Closed                |
|------------------|--------------------------|----------------------------|
| Priority          | Availability             | Confidentiality/Integrity  |
| Suitable For      | Public-access systems     | Critical/regulated systems |

---

## 5. Security Recommendations

- Use **passive monitoring** for detection and logging; **active controls** for enforcement.
- Deploy **inline devices** with **redundant paths** and failover mechanisms.
- Always document and test **fail-open vs. fail-closed** behavior under various scenarios.
- For forensic reliability, prefer **TAPs** over SPAN ports.
- Restrict and audit configuration access to SPAN ports and inline devices.
- Monitor and maintain physical security of TAPs and inline hardware.

---
