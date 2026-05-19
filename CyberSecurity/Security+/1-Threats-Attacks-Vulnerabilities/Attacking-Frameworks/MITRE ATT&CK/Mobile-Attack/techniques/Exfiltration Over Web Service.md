---
alias: T1567
---

## T1567

Adversaries may use an existing, legitimate external Web service to exfiltrate data rather than their primary command and control channel. Popular Web services acting as an exfiltration mechanism may give a significant amount of cover due to the likelihood that hosts within a network are already communicating with them prior to compromise. Firewall rules may also already exist to permit traffic to these services.

Web service providers also commonly use SSL/TLS encryption, giving adversaries an added level of protection.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Exfiltration]] (TA0010)

### Platforms
- Linux
- macOS
- Windows
- Office 365
- SaaS
- Google Workspace

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict Web-Based Content\|M1021]] | Restrict Web-Based Content | Web proxies can be used to enforce an external network communication policy that prevents use of unauthorized external services. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Data Loss Prevention\|M1057]] | Data Loss Prevention | Data loss prevention can be detect and block sensitive data being uploaded to web services via web browsers. |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Exfiltration Over Webhook\|T1567.004]] | Exfiltration Over Webhook |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Exfiltration to Code Repository\|T1567.001]] | Exfiltration to Code Repository |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Exfiltration to Text Storage Sites\|T1567.003]] | Exfiltration to Text Storage Sites |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Exfiltration to Cloud Storage\|T1567.002]] | Exfiltration to Cloud Storage |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1567
