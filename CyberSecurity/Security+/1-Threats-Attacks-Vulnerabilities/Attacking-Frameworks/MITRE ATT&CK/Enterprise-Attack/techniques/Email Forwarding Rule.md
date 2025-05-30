---
alias: T1114.003
---

## T1114.003

Adversaries may setup email forwarding rules to collect sensitive information. Adversaries may abuse email forwarding rules to monitor the activities of a victim, steal information, and further gain intelligence on the victim or the victim’s organization to use as part of further exploits or operations.(Citation: US-CERT TA18-068A 2018) Furthermore, email forwarding rules can allow adversaries to maintain persistent access to victim's emails even after compromised credentials are reset by administrators.(Citation: Pfammatter - Hidden Inbox Rules) Most email clients allow users to create inbox rules for various email functions, including forwarding to a different recipient. These rules may be created through a local email application, a web interface, or by command-line interface. Messages can be forwarded to internal or external recipients, and there are no restrictions limiting the extent of this rule. Administrators may also create forwarding rules for user accounts with the same considerations and outcomes.(Citation: Microsoft Tim McMichael Exchange Mail Forwarding 2)(Citation: Mac Forwarding Rules)

Any user or administrator within the organization (or adversary with valid credentials) can create rules to automatically forward all received messages to another recipient, forward emails to different locations based on the sender, and more. Adversaries may also hide the rule by making use of the Microsoft Messaging API (MAPI) to modify the rule properties, making it hidden and not visible from Outlook, OWA or most Exchange Administration tools.(Citation: Pfammatter - Hidden Inbox Rules)

In some environments, administrators may be able to enable email forwarding rules that operate organization-wide rather than on individual inboxes. For example, Microsoft Exchange supports transport rules that evaluate all mail an organization receives against user-specified conditions, then performs a user-specified action on mail that adheres to those conditions.(Citation: Microsoft Mail Flow Rules 2023) Adversaries that abuse such features may be able to enable forwarding on all or specific mail an organization receives. 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Collection]] (TA0009)

### Platforms
- Office 365
- Windows
- Google Workspace
- macOS
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Enterprise email solutions have monitoring mechanisms that may include the ability to audit auto-forwarding rules on a regular basis.<br /><br />In an Exchange environment, Administrators can use `Get-InboxRule` / `Remove-InboxRule` and `Get-TransportRule` / `Remove-TransportRule` to discover and remove potentially malicious auto-fowarding and transport rules.(Citation: Microsoft Tim McMichael Exchange Mail Forwarding 2)(Citation: Microsoft Manage Mail Flow Rules 2023)(Citation: Microsoft Get-InboxRule) In addition to this, a MAPI Editor can be utilized to examine the underlying database structure and discover any modifications/tampering of the properties of auto-forwarding rules.(Citation: Pfammatter - Hidden Inbox Rules) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Consider disabling external email forwarding.(Citation: Microsoft BEC Campaign) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Use of encryption provides an added layer of security to sensitive information sent over email. Encryption using public key cryptography requires the adversary to obtain the private certificate along with an encryption key to decrypt messages. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1114/003
- Mac Forwarding Rules: https://support.apple.com/guide/mail/reply-to-forward-or-redirect-emails-mlhlp1010/mac
- Pfammatter - Hidden Inbox Rules: https://blog.compass-security.com/2018/09/hidden-inbox-rules-in-microsoft-exchange/
- Microsoft Tim McMichael Exchange Mail Forwarding 2: https://blogs.technet.microsoft.com/timmcmic/2015/06/08/exchange-and-office-365-mail-forwarding-2/
- Microsoft Mail Flow Rules 2023: https://learn.microsoft.com/en-us/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules
- US-CERT TA18-068A 2018: https://www.us-cert.gov/ncas/alerts/TA18-086A
