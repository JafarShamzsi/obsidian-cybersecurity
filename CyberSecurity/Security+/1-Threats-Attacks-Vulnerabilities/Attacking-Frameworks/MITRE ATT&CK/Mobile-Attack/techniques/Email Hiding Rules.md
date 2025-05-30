---
alias: T1564.008
---

## T1564.008

Adversaries may use email rules to hide inbound emails in a compromised user's mailbox. Many email clients allow users to create inbox rules for various email functions, including moving emails to other folders, marking emails as read, or deleting emails. Rules may be created or modified within email clients or through external features such as the <code>New-InboxRule</code> or <code>Set-InboxRule</code> [PowerShell](https://attack.mitre.org/techniques/T1059/001) cmdlets on Windows systems.(Citation: Microsoft Inbox Rules)(Citation: MacOS Email Rules)(Citation: Microsoft New-InboxRule)(Citation: Microsoft Set-InboxRule)

Adversaries may utilize email rules within a compromised user's mailbox to delete and/or move emails to less noticeable folders. Adversaries may do this to hide security alerts, C2 communication, or responses to [Internal Spearphishing](https://attack.mitre.org/techniques/T1534) emails sent from the compromised account.

Any user or administrator within the organization (or adversary with valid credentials) may be able to create rules to automatically move or delete emails. These rules can be abused to impair/delay detection had the email content been immediately seen by a user or defender. Malicious rules commonly filter out emails based on key words (such as <code>malware</code>, <code>suspicious</code>, <code>phish</code>, and <code>hack</code>) found in message bodies and subject lines. (Citation: Microsoft Cloud App Security)

In some environments, administrators may be able to enable email rules that operate organization-wide rather than on individual inboxes. For example, Microsoft Exchange supports transport rules that evaluate all mail an organization receives against user-specified conditions, then performs a user-specified action on mail that adheres to those conditions.(Citation: Microsoft Mail Flow Rules 2023) Adversaries that abuse such features may be able to automatically modify or delete all emails related to specific topics (such as internal security incident notifications).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows
- Office 365
- Linux
- macOS
- Google Workspace

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Enterprise email solutions may have monitoring mechanisms that may include the ability to audit inbox rules on a regular basis. <br /><br />In an Exchange environment, Administrators can use `Get-InboxRule` / `Remove-InboxRule` and `Get-TransportRule` / `Remove-TransportRule` to discover and remove potentially malicious inbox and transport rules.(Citation: Microsoft Get-InboxRule)(Citation: Microsoft Manage Mail Flow Rules 2023) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1564/008
- MacOS Email Rules: https://support.apple.com/guide/mail/use-rules-to-manage-emails-you-receive-mlhlp1017/mac
- Microsoft BEC Campaign: https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/
- Microsoft Mail Flow Rules 2023: https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules
- Microsoft Inbox Rules: https://support.microsoft.com/en-us/office/manage-email-messages-by-using-rules-c24f5dea-9465-4df4-ad17-a50704d66c59
- Microsoft New-InboxRule: https://docs.microsoft.com/en-us/powershell/module/exchange/new-inboxrule?view=exchange-ps
- Microsoft Set-InboxRule: https://docs.microsoft.com/en-us/powershell/module/exchange/set-inboxrule?view=exchange-ps
- Microsoft Cloud App Security: https://techcommunity.microsoft.com/t5/security-compliance-and-identity/rule-your-inbox-with-microsoft-cloud-app-security/ba-p/299154
