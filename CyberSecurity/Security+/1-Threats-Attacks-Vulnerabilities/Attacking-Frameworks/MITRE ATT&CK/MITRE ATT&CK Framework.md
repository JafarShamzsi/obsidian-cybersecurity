## Overview

The MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) framework is a globally recognized knowledge base that catalogs the tactics and techniques used by cyber adversaries. It helps organizations understand, detect, and respond to cyber threats effectively.

## Structure of MITRE ATT&CK

MITRE ATT&CK is structured into several key components:

### 1. **Tactics** (Why the attacker acts)

Tactics represent the high-level objectives that adversaries are trying to achieve during an attack. These align with different phases of an attack lifecycle. Examples include:

- Initial Access
    
- Execution
    
- Persistence
    
- Privilege Escalation
    
- Defense Evasion
    
- Credential Access
    
- Discovery
    
- Lateral Movement
    
- Collection
    
- Exfiltration
    
- Impact
    

### 2. **Techniques & Sub-Techniques** (How the attacker acts)

Techniques describe the specific methods adversaries use to achieve their objectives. Each technique can have multiple sub-techniques that provide further granularity. Examples include:

- **Credential Dumping (T1003)** – Extracting credentials from OS memory.
    
- **Spear Phishing (T1566)** – Sending targeted phishing emails.
    
- **Living off the Land (T1218)** – Abusing legitimate system tools to avoid detection.
    

### 3. **Procedures** (Real-world implementations)

Procedures provide real-world examples of how specific threat groups or malware families use techniques.

## MITRE ATT&CK Matrices

MITRE ATT&CK is divided into different matrices, including:

1. **Enterprise ATT&CK** – Focused on Windows, macOS, Linux, and cloud environments.
    
2. **Mobile ATT&CK** – Focused on threats against mobile devices.
    
3. **ICS ATT&CK** – Focused on Industrial Control Systems (ICS) and operational technology environments.
    

## Applications of MITRE ATT&CK

Organizations use the MITRE ATT&CK framework for multiple cybersecurity purposes, such as:

- **Threat Detection & Hunting** – Mapping adversary behaviors to known techniques.
    
- **Incident Response** – Understanding and mitigating attacks effectively.
    
- **Red Teaming** – Simulating real-world attack scenarios for security assessments.
    
- **Security Operations & SIEM Rules** – Creating detection rules for monitoring tools.
    

## ATT&CK Navigator

MITRE provides the ATT&CK Navigator, a web-based tool that allows security professionals to visualize and map techniques based on their environment, aiding in threat modeling and defense strategy planning.

## MITRE ATT&CK vs. Other Attack Frameworks

- **Compared to Cyber Kill Chain:** ATT&CK provides a more granular breakdown of techniques.
    
- **Compared to Diamond Model:** ATT&CK focuses on adversary behaviors, while the Diamond Model emphasizes relationships between entities.
    
- **Compared to STRIDE:** STRIDE is more focused on threat modeling during system design, while ATT&CK is used for detecting and responding to threats.
    

## Conclusion

MITRE ATT&CK is a valuable tool for cybersecurity professionals to analyze, understand, and mitigate threats. By leveraging ATT&CK, organizations can strengthen their security posture, enhance threat intelligence, and improve incident response strategies.

---

### Related Notes

- [[Cyber Kill Chain Framework]]

- [[Diamond Model of Intrusion Analysis]]

- [[STRIDE Threat Model]]