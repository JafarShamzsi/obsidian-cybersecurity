---
alias: Threat Group-1314, TG-1314
---

## G0028

[Threat Group-1314](https://attack.mitre.org/groups/G0028) is an unattributed threat group that has used compromised credentials to log into a victim's remote access infrastructure. (Citation: Dell TG-1314)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/SMB／Windows Admin Shares\|T1021.002]] | SMB／Windows Admin Shares | [Threat Group-1314](https://attack.mitre.org/groups/G0028) actors mapped network drives using <code>net use</code>.(Citation: Dell TG-1314) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Windows Command Shell\|T1059.003]] | Windows Command Shell | [Threat Group-1314](https://attack.mitre.org/groups/G0028) actors spawned shells on remote systems on a victim network to execute commands.(Citation: Dell TG-1314) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Software Deployment Tools\|T1072]] | Software Deployment Tools | [Threat Group-1314](https://attack.mitre.org/groups/G0028) actors used a victim's endpoint management platform, Altiris, for lateral movement.(Citation: Dell TG-1314) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Domain Accounts\|T1078.002]] | Domain Accounts | [Threat Group-1314](https://attack.mitre.org/groups/G0028) actors used compromised domain credentials for the victim's endpoint management platform, Altiris, to move laterally.(Citation: Dell TG-1314) |
