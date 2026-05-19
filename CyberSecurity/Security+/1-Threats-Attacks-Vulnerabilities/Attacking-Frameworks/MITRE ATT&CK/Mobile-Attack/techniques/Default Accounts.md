---
alias: T1078.001
---

## T1078.001

Adversaries may obtain and abuse credentials of a default account as a means of gaining Initial Access, Persistence, Privilege Escalation, or Defense Evasion. Default accounts are those that are built-into an OS, such as the Guest or Administrator accounts on Windows systems. Default accounts also include default factory/provider set accounts on other types of systems, software, or devices, including the root user account in AWS and the default service account in Kubernetes.(Citation: Microsoft Local Accounts Feb 2019)(Citation: AWS Root User)(Citation: Threat Matrix for Kubernetes)

Default accounts are not limited to client machines, rather also include accounts that are preset for equipment such as network devices and computer applications whether they are internal, open source, or commercial. Appliances that come preset with a username and password combination pose a serious threat to organizations that do not change it post installation, as they are easy targets for an adversary. Similarly, adversaries may also utilize publicly disclosed or stolen [Private Keys](https://attack.mitre.org/techniques/T1552/004) or credential materials to legitimately connect to remote environments via [Remote Services](https://attack.mitre.org/techniques/T1021).(Citation: Metasploit SSH Module)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Privilege Escalation]] (TA0004)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Initial Access]] (TA0001)

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
- Network

### Permissions Required
- Administrator
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Applications and appliances that utilize default username and password should be changed immediately after the installation, and before deployment to a production environment. (Citation: US-CERT Alert TA13-175A Risks of Default Passwords on the Internet) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1078/001
- AWS Root User: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_root-user.html
- Microsoft Local Accounts Feb 2019: https://docs.microsoft.com/en-us/windows/security/identity-protection/access-control/local-accounts
- Metasploit SSH Module: https://github.com/rapid7/metasploit-framework/tree/master/modules/exploits/linux/ssh
- Threat Matrix for Kubernetes: https://www.microsoft.com/security/blog/2020/04/02/attack-matrix-kubernetes/
