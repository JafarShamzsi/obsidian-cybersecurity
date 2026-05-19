---
alias: T1573
---

## T1573

Adversaries may employ an encryption algorithm to conceal command and control traffic rather than relying on any inherent protections provided by a communication protocol. Despite the use of a secure algorithm, these implementations may be vulnerable to reverse engineering if secret keys are encoded and/or generated within malware samples/configuration files.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Command and Control]] (TA0011)

### Platforms
- Linux
- macOS
- Windows
- Network

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Network intrusion detection and prevention systems that use network signatures to identify traffic for specific adversary malware can be used to mitigate activity at the network level. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/SSL／TLS Inspection\|M1020]] | SSL／TLS Inspection | SSL/TLS inspection can be used to see the contents of encrypted sessions to look for network-based indicators of malware communication protocols. |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Symmetric Cryptography\|T1573.001]] | Symmetric Cryptography |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Asymmetric Cryptography\|T1573.002]] | Asymmetric Cryptography |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1573
- SANS Decrypting SSL: http://www.sans.org/reading-room/whitepapers/analyst/finding-hidden-threats-decrypting-ssl-34840
- SEI SSL Inspection Risks: https://insights.sei.cmu.edu/cert/2015/03/the-risks-of-ssl-inspection.html
- University of Birmingham C2: https://arxiv.org/ftp/arxiv/papers/1408/1408.1136.pdf
