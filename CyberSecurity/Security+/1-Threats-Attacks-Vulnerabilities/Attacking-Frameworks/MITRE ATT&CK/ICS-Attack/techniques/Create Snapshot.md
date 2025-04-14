---
alias: T1578.001
---

## T1578.001

An adversary may create a snapshot or data backup within a cloud account to evade defenses. A snapshot is a point-in-time copy of an existing cloud compute component such as a virtual machine (VM), virtual hard drive, or volume. An adversary may leverage permissions to create a snapshot in order to bypass restrictions that prevent access to existing compute service infrastructure, unlike in [Revert Cloud Instance](https://attack.mitre.org/techniques/T1578/004) where an adversary may revert to a snapshot to evade detection and remove evidence of their presence.

An adversary may [Create Cloud Instance](https://attack.mitre.org/techniques/T1578/002), mount one or more created snapshots to that instance, and then apply a policy that allows the adversary access to the created instance, such as a firewall policy that allows them inbound and outbound SSH access.(Citation: Mandiant M-Trends 2020)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- IaaS

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit permissions for creating snapshots or backups in accordance with least privilege. Organizations should limit the number of users within the organization with an IAM role that has administrative privileges, strive to reduce all permanent privileged role assignments, and conduct periodic entitlement reviews on IAM users, roles and policies.(Citation: Mandiant M-Trends 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Routinely check user permissions to ensure only the expected users have the capability to create snapshots and backups. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1578/001
- Mandiant M-Trends 2020: https://content.fireeye.com/m-trends/rpt-m-trends-2020
- AWS Cloud Trail Backup API: https://docs.aws.amazon.com/aws-backup/latest/devguide/logging-using-cloudtrail.html
- Azure - Monitor Logs: https://docs.microsoft.com/en-us/azure/backup/backup-azure-monitoring-use-azuremonitor
- Cloud Audit Logs: https://cloud.google.com/logging/docs/audit#admin-activity
- GCP - Creating and Starting a VM: https://cloud.google.com/compute/docs/instances/create-start-instance#api_2
