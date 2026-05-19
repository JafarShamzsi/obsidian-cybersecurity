---
alias: Strider, ProjectSauron
---

## G0041

[Strider](https://attack.mitre.org/groups/G0041) is a threat group that has been active since at least 2011 and has targeted victims in Russia, China, Sweden, Belgium, Iran, and Rwanda.(Citation: Symantec Strider Blog)(Citation: Kaspersky ProjectSauron Blog)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Internal Proxy\|T1090.001]] | Internal Proxy | [Strider](https://attack.mitre.org/groups/G0041) has used local servers with both local network and Internet access to act as internal proxy nodes to exfiltrate data from other parts of the network without direct Internet access.(Citation: Kaspersky ProjectSauron Blog) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Password Filter DLL\|T1556.002]] | Password Filter DLL | [Strider](https://attack.mitre.org/groups/G0041) has registered its persistence module on domain controllers as a Windows LSA (Local System Authority) password filter to acquire credentials any time a domain, local user, or administrator logs in or changes a password.(Citation: Kaspersky ProjectSauron Full Report) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Hidden File System\|T1564.005]] | Hidden File System | [Strider](https://attack.mitre.org/groups/G0041) has used a hidden file system that is stored as a file on disk.(Citation: Kaspersky ProjectSauron Full Report) |
