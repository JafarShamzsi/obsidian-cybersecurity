---
alias: T1213.003
---

## T1213.003

Adversaries may leverage code repositories to collect valuable information. Code repositories are tools/services that store source code and automate software builds. They may be hosted internally or privately on third party sites such as Github, GitLab, SourceForge, and BitBucket. Users typically interact with code repositories through a web application or command-line utilities such as git.

Once adversaries gain access to a victim network or a private code repository, they may collect sensitive information such as proprietary source code or credentials contained within software's source code.  Having access to software's source code may allow adversaries to develop [Exploits](https://attack.mitre.org/techniques/T1587/004), while credentials may provide access to additional resources using [Valid Accounts](https://attack.mitre.org/techniques/T1078).(Citation: Wired Uber Breach)(Citation: Krebs Adobe)

**Note:** This is distinct from [Code Repositories](https://attack.mitre.org/techniques/T1593/003), which focuses on conducting [Reconnaissance](https://attack.mitre.org/tactics/TA0043) via public code repositories.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Collection]] (TA0009)

### Platforms
- SaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Training\|M1017]] | User Training | Develop and publish policies that define acceptable information to be stored in code repositories. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Enforce the principle of least-privilege. Consider implementing access control mechanisms that include both authentication and authorization for code repositories. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Use multi-factor authentication for logons to code repositories. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Consider periodic reviews of accounts and privileges for critical and sensitive code repositories. Scan code repositories for exposed credentials or other sensitive information. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1213/003
- Wired Uber Breach: https://www.wired.com/story/uber-paid-off-hackers-to-hide-a-57-million-user-data-breach/
- Krebs Adobe: https://krebsonsecurity.com/2013/10/adobe-to-announce-source-code-customer-data-breach/
