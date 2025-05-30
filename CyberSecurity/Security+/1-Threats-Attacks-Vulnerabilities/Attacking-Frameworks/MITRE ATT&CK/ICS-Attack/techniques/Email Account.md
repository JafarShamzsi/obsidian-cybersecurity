---
alias: T1087.003
---

## T1087.003

Adversaries may attempt to get a listing of email addresses and accounts. Adversaries may try to dump Exchange address lists such as global address lists (GALs).(Citation: Microsoft Exchange Address Lists)

In on-premises Exchange and Exchange Online, the<code>Get-GlobalAddressList</code> PowerShell cmdlet can be used to obtain email addresses and accounts from a domain using an authenticated session.(Citation: Microsoft getglobaladdresslist)(Citation: Black Hills Attacking Exchange MailSniper, 2016)

In Google Workspace, the GAL is shared with Microsoft Outlook users through the Google Workspace Sync for Microsoft Outlook (GWSMO) service. Additionally, the Google Workspace Directory allows for users to get a listing of other users within the organization.(Citation: Google Workspace Global Access List)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows
- Office 365
- Google Workspace

### Permissions Required
- User

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1087/003
- Microsoft Exchange Address Lists: https://docs.microsoft.com/en-us/exchange/email-addresses-and-address-books/address-lists/address-lists?view=exchserver-2019
- Microsoft getglobaladdresslist: https://docs.microsoft.com/en-us/powershell/module/exchange/email-addresses-and-address-books/get-globaladdresslist
- Black Hills Attacking Exchange MailSniper, 2016: https://www.blackhillsinfosec.com/attacking-exchange-with-mailsniper/
- Google Workspace Global Access List: https://support.google.com/a/answer/166870?hl=en
