---
alias: T1578.003
---

## T1578.003

An adversary may delete a cloud instance after they have performed malicious activities in an attempt to evade detection and remove evidence of their presence.  Deleting an instance or virtual machine can remove valuable forensic artifacts and other evidence of suspicious behavior if the instance is not recoverable.

An adversary may also [Create Cloud Instance](https://attack.mitre.org/techniques/T1578/002) and later terminate the instance after achieving their objectives.(Citation: Mandiant M-Trends 2020)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- IaaS

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit permissions for deleting new instances in accordance with least privilege. Organizations should limit the number of users within the organization with an IAM role that has administrative privileges, strive to reduce all permanent privileged role assignments, and conduct periodic entitlement reviews on IAM users, roles and policies.(Citation: Mandiant M-Trends 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Routinely check user permissions to ensure only the expected users have the capability to delete new instances. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1578/003
- Mandiant M-Trends 2020: https://content.fireeye.com/m-trends/rpt-m-trends-2020
- AWS CloudTrail Search: https://aws.amazon.com/premiumsupport/knowledge-center/cloudtrail-search-api-calls/
- Azure Activity Logs: https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/view-activity-logs
- Cloud Audit Logs: https://cloud.google.com/logging/docs/audit#admin-activity
