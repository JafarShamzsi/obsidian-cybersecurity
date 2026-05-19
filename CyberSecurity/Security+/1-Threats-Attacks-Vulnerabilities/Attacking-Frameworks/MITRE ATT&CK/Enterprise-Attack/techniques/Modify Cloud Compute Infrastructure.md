---
alias: T1578
---

## T1578

An adversary may attempt to modify a cloud account's compute service infrastructure to evade defenses. A modification to the compute service infrastructure can include the creation, deletion, or modification of one or more components such as compute instances, virtual machines, and snapshots.

Permissions gained from the modification of infrastructure components may bypass restrictions that prevent access to existing infrastructure. Modifying infrastructure components may also allow an adversary to evade detection and remove evidence of their presence.(Citation: Mandiant M-Trends 2020)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit permissions for creating, deleting, and otherwise altering compute components in accordance with least privilege. Organizations should limit the number of users within the organization with an IAM role that has administrative privileges, strive to reduce all permanent privileged role assignments, and conduct periodic entitlement reviews on IAM users, roles and policies.(Citation: Mandiant M-Trends 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Routinely monitor user permissions to ensure only the expected users have the capability to modify cloud compute infrastructure components. |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Revert Cloud Instance\|T1578.004]] | Revert Cloud Instance |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Delete Cloud Instance\|T1578.003]] | Delete Cloud Instance |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Modify Cloud Compute Configurations\|T1578.005]] | Modify Cloud Compute Configurations |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Create Cloud Instance\|T1578.002]] | Create Cloud Instance |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Create Snapshot\|T1578.001]] | Create Snapshot |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1578
- Mandiant M-Trends 2020: https://content.fireeye.com/m-trends/rpt-m-trends-2020
