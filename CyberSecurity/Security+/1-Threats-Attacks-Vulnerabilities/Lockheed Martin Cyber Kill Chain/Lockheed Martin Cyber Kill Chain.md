## Overview

The **Lockheed Martin Cyber Kill Chain** is a model developed to understand and prevent cyber intrusions by analyzing the stages of a cyber attack. It consists of seven phases that adversaries follow to compromise systems. Understanding each phase helps defenders implement countermeasures at every step of an attack.

![[Pasted image 20250327024644.png]]

## The Seven Phases of the Cyber Kill Chain

### 1. **Reconnaissance**

- The attacker gathers information about the target.
- This can involve:
    - Open-source intelligence (OSINT)
    - Scanning networks for vulnerabilities
    - Phishing attempts to gather credentials
- **Defense Measures:**
    - Implement external network monitoring
    - Restrict publicly available sensitive information
    - Conduct security awareness training to prevent social engineering

### 2. **Weaponization**

- The attacker creates a malicious payload based on the gathered information.
- This can involve:
    - Developing malware (e.g., trojans, ransomware, keyloggers)
    - Crafting exploit kits to take advantage of known vulnerabilities
- **Defense Measures:**
    - Keep software and systems up to date
    - Use threat intelligence feeds to identify new exploits
    - Deploy advanced endpoint detection systems

### 3. **Delivery**

- The attacker transmits the weaponized payload to the victim.
- Common delivery methods include:
    - Phishing emails with malicious attachments or links
    - Drive-by downloads from compromised websites
    - USB devices or other removable media
- **Defense Measures:**
    - Implement email filtering and anti-phishing tools
    - Use web filtering to block malicious domains
    - Restrict the use of removable media in enterprise environments

### 4. **Exploitation**

- The attacker executes the exploit, taking advantage of a system vulnerability.
- This can include:
    - Exploiting outdated software or unpatched vulnerabilities
    - Gaining remote access via zero-day exploits
- **Defense Measures:**
    - Apply security patches and updates regularly
    - Implement host-based intrusion detection and prevention systems (HIDS/HIPS)
    - Use application whitelisting to prevent unauthorized executions

### 5. **Installation**

- The attacker establishes persistence on the compromised system.
- This can involve:
    - Installing backdoors, rootkits, or trojans
    - Modifying registry keys or scheduled tasks to maintain access
- **Defense Measures:**
    - Monitor for unauthorized software installations
    - Conduct regular system integrity checks
    - Deploy endpoint detection and response (EDR) solutions

### 6. **Command and Control (C2)**

- The compromised system connects to an external attacker-controlled server.
- This enables:
    - Remote execution of commands
    - Exfiltration of sensitive data
    - Deployment of additional payloads
- **Defense Measures:**
    - Monitor network traffic for anomalies and beaconing behavior
    - Block known malicious IP addresses and domains
    - Use anomaly detection systems and AI-driven analytics

### 7. **Actions on Objectives**

- The attacker executes the final goal, such as:
    - Data theft (data exfiltration)
    - System destruction or ransomware deployment
    - Lateral movement to additional targets
- **Defense Measures:**
    - Implement data loss prevention (DLP) solutions
    - Use behavior-based anomaly detection to identify insider threats
    - Ensure network segmentation to limit movement within the network

## Importance of the Cyber Kill Chain

- Helps security teams **identify attack patterns** and **disrupt attacks at each stage**.
- Enhances **incident response** by mapping detected threats to a structured attack framework.
- Supports **proactive defense** by integrating the model into security architectures and SOC workflows.

## Limitations

- Focuses primarily on **external threats** rather than insider threats.
- May not account for **modern attack techniques** such as fileless malware or living-off-the-land attacks (LOTL).
- Does not address **supply chain attacks** effectively.

## Conclusion

The **Cyber Kill Chain** remains a valuable model for understanding cyber attacks and enhancing security posture. When combined with frameworks like **MITRE ATT&CK** and **NIST CSF**, it provides a robust foundation for threat detection and response.

---

**Related Notes:**

- [[MITRE ATT&CK Framework]]
- [[NIST Cybersecurity Framework]]
- Cyber Threat Intelligence (CTI)