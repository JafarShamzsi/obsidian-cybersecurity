---
alias: T1562.010
---

## T1562.010

Adversaries may downgrade or use a version of system features that may be outdated, vulnerable, and/or does not support updated security controls. Downgrade attacks typically take advantage of a system’s backward compatibility to force it into less secure modes of operation. 

Adversaries may downgrade and use various less-secure versions of features of a system, such as [Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059)s or even network protocols that can be abused to enable [Adversary-in-the-Middle](https://attack.mitre.org/techniques/T1557) or [Network Sniffing](https://attack.mitre.org/techniques/T1040).(Citation: Praetorian TLS Downgrade Attack 2014) For example, [PowerShell](https://attack.mitre.org/techniques/T1059/001) versions 5+ includes Script Block Logging (SBL) which can record executed script content. However, adversaries may attempt to execute a previous version of PowerShell that does not support SBL with the intent to [Impair Defenses](https://attack.mitre.org/techniques/T1562) while running malicious scripts that may have otherwise been detected.(Citation: CrowdStrike BGH Ransomware 2021)(Citation: Mandiant BYOL 2018)(Citation: att_def_ps_logging)

Adversaries may similarly target network traffic to downgrade from an encrypted HTTPS connection to an unsecured HTTP connection that exposes network data in clear text.(Citation: Targeted SSL Stripping Attacks Are Real)(Citation: Crowdstrike Downgrade)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows
- Linux
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Consider implementing policies on internal web servers, such HTTP Strict Transport Security, that enforce the use of HTTPS/network traffic encryption to prevent insecure connections.(Citation: Chromium HSTS) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Consider removing previous versions of tools that are unnecessary to the environment when possible. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1562/010
- Crowdstrike Downgrade: https://www.crowdstrike.com/cybersecurity-101/attack-types/downgrade-attacks/
- Targeted SSL Stripping Attacks Are Real: https://blog.checkpoint.com/research/targeted-ssl-stripping-attacks-are-real/amp/
- CrowdStrike BGH Ransomware 2021: https://www.crowdstrike.com/blog/how-falcon-complete-stopped-a-big-game-hunting-ransomware-attack/
- att_def_ps_logging: https://nsfocusglobal.com/attack-and-defense-around-powershell-event-logging/
- inv_ps_attacks: https://powershellmagazine.com/2014/07/16/investigating-powershell-attacks/
- Mandiant BYOL 2018: https://www.mandiant.com/resources/bring-your-own-land-novel-red-teaming-technique
- Praetorian TLS Downgrade Attack 2014: https://www.praetorian.com/blog/man-in-the-middle-tls-ssl-protocol-downgrade-attack/
