---
alias: T1069
---

## T1069

Adversaries may attempt to discover group and permission settings. This information can help adversaries determine which user accounts and groups are available, the membership of users in particular groups, and which users and groups have elevated permissions.

Adversaries may attempt to discover group permission settings in many different ways. This data may provide the adversary with information about the compromised environment that can be used in follow-on activity and targeting.(Citation: CrowdStrike BloodHound April 2018)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows
- Azure AD
- Office 365
- SaaS
- IaaS
- Linux
- macOS
- Google Workspace
- Containers

### Permissions Required

### Mitigations

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Cloud Groups\|T1069.003]] | Cloud Groups |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Domain Groups\|T1069.002]] | Domain Groups |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Local Groups\|T1069.001]] | Local Groups |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1069
- K8s Authorization Overview: https://kubernetes.io/docs/reference/access-authn-authz/authorization/
- CrowdStrike BloodHound April 2018: https://www.crowdstrike.com/blog/hidden-administrative-accounts-bloodhound-to-the-rescue/
