---
alias: T1589.002
---

## T1589.002

Adversaries may gather email addresses that can be used during targeting. Even if internal instances exist, organizations may have public-facing email infrastructure and addresses for employees.

Adversaries may easily gather email addresses, since they may be readily available and exposed via online or other accessible data sets (ex: [Social Media](https://attack.mitre.org/techniques/T1593/001) or [Search Victim-Owned Websites](https://attack.mitre.org/techniques/T1594)).(Citation: HackersArise Email)(Citation: CNET Leaks) Email addresses could also be enumerated via more active means (i.e. [Active Scanning](https://attack.mitre.org/techniques/T1595)), such as probing and analyzing responses from authentication services that may reveal valid usernames in a system.(Citation: GrimBlog UsernameEnum) For example, adversaries may be able to enumerate email addresses in Office 365 environments by querying a variety of publicly available API endpoints, such as autodiscover and GetCredentialType.(Citation: GitHub Office 365 User Enumeration)(Citation: Azure Active Directory Reconnaisance)

Gathering this information may reveal opportunities for other forms of reconnaissance (ex: [Search Open Websites/Domains](https://attack.mitre.org/techniques/T1593) or [Phishing for Information](https://attack.mitre.org/techniques/T1598)), establishing operational resources (ex: [Email Accounts](https://attack.mitre.org/techniques/T1586/002)), and/or initial access (ex: [Phishing](https://attack.mitre.org/techniques/T1566) or [Brute Force](https://attack.mitre.org/techniques/T1110) via [External Remote Services](https://attack.mitre.org/techniques/T1133)).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Reconnaissance]] (TA0043)

### Platforms
- PRE

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Pre-compromise\|M1056]] | Pre-compromise | This technique cannot be easily mitigated with preventive controls since it is based on behaviors performed outside of the scope of enterprise defenses and controls. Efforts should focus on minimizing the amount and sensitivity of data available to external parties. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1589/002
- Azure Active Directory Reconnaisance: https://o365blog.com/post/just-looking/
- GitHub Office 365 User Enumeration: https://github.com/gremwell/o365enum
- GrimBlog UsernameEnum: https://grimhacker.com/2017/07/24/office365-activesync-username-enumeration/
- HackersArise Email: https://www.hackers-arise.com/email-scraping-and-maltego
- CNET Leaks: https://www.cnet.com/news/massive-breach-leaks-773-million-emails-21-million-passwords/
