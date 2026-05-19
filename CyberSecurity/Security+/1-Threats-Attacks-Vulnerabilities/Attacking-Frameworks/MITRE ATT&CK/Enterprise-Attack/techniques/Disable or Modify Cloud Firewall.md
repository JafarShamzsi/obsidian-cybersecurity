---
alias: T1562.007
---

## T1562.007

Adversaries may disable or modify a firewall within a cloud environment to bypass controls that limit access to cloud resources. Cloud firewalls are separate from system firewalls that are described in [Disable or Modify System Firewall](https://attack.mitre.org/techniques/T1562/004). 

Cloud environments typically utilize restrictive security groups and firewall rules that only allow network activity from trusted IP addresses via expected ports and protocols. An adversary may introduce new firewall rules or policies to allow access into a victim cloud environment. For example, an adversary may use a script or utility that creates new ingress rules in existing security groups to allow any TCP/IP connectivity, or remove networking limitations to support traffic associated with malicious activity (such as cryptomining).(Citation: Expel IO Evil in AWS)(Citation: Palo Alto Unit 42 Compromised Cloud Compute Credentials 2022)

Modifying or disabling a cloud firewall may enable adversary C2 communications, lateral movement, and/or data exfiltration that would otherwise not be allowed.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Ensure least privilege principles are applied to Identity and Access Management (IAM) security policies.(Citation: Expel IO Evil in AWS) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Routinely check account role permissions to ensure only expected users and roles have permission to modify cloud firewalls.  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1562/007
- Expel IO Evil in AWS: https://expel.io/blog/finding-evil-in-aws/
- Palo Alto Unit 42 Compromised Cloud Compute Credentials 2022: https://unit42.paloaltonetworks.com/compromised-cloud-compute-credentials/
