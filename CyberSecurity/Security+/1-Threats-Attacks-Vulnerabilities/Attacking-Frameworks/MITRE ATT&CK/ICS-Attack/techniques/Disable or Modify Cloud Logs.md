---
alias: T1562.008
---

## T1562.008

An adversary may disable or modify cloud logging capabilities and integrations to limit what data is collected on their activities and avoid detection. Cloud environments allow for collection and analysis of audit and application logs that provide insight into what activities a user does within the environment. If an adversary has sufficient permissions, they can disable or modify logging to avoid detection of their activities.

For example, in AWS an adversary may disable CloudWatch/CloudTrail integrations prior to conducting further malicious activity.(Citation: Following the CloudTrail: Generating strong AWS security signals with Sumo Logic) They may alternatively tamper with logging functionality – for example, by removing any associated SNS topics, disabling multi-region logging, or disabling settings that validate and/or encrypt log files.(Citation: AWS Update Trail)(Citation: Pacu Detection Disruption Module) In Office 365, an adversary may disable logging on mail collection activities for specific users by using the `Set-MailboxAuditBypassAssociation` cmdlet, by disabling M365 Advanced Auditing for the user, or by downgrading the user’s license from an Enterprise E5 to an Enterprise E3 license.(Citation: Dark Reading Microsoft 365 Attacks 2021)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- IaaS
- SaaS
- Google Workspace
- Azure AD
- Office 365

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Configure default account policy to enable logging. Manage policies to ensure only necessary users have permissions to make changes to logging policies. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1562/008
- Stopping CloudTrail from Sending Events to CloudWatch Logs: https://docs.aws.amazon.com/awscloudtrail/latest/userguide/stop-cloudtrail-from-sending-events-to-cloudwatch-logs.html
- AWS Update Trail: https://awscli.amazonaws.com/v2/documentation/api/latest/reference/cloudtrail/update-trail.html
- Following the CloudTrail: Generating strong AWS security signals with Sumo Logic: https://expel.io/blog/following-cloudtrail-generating-aws-security-signals-sumo-logic/
- Configuring Data Access audit logs: https://cloud.google.com/logging/docs/audit/configure-data-access
- Dark Reading Microsoft 365 Attacks 2021: https://www.darkreading.com/threat-intelligence/incident-responders-explore-microsoft-365-attacks-in-the-wild/d/d-id/1341591
- az monitor diagnostic-settings: https://docs.microsoft.com/en-us/cli/azure/monitor/diagnostic-settings?view=azure-cli-latest#az_monitor_diagnostic_settings_delete
- Pacu Detection Disruption Module: https://github.com/RhinoSecurityLabs/pacu/blob/master/pacu/modules/detection__disruption/main.py
