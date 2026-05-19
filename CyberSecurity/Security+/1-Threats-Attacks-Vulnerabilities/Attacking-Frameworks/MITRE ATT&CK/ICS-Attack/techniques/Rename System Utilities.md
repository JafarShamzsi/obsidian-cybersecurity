---
alias: T1036.003
---

## T1036.003

Adversaries may rename legitimate system utilities to try to evade security mechanisms concerning the usage of those utilities. Security monitoring and control mechanisms may be in place for system utilities adversaries are capable of abusing. (Citation: LOLBAS Main Site) It may be possible to bypass those security mechanisms by renaming the utility prior to utilization (ex: rename <code>rundll32.exe</code>). (Citation: Elastic Masquerade Ball) An alternative case occurs when a legitimate utility is copied or moved to a different directory and renamed to avoid detections based on system utilities executing from non-standard paths. (Citation: F-Secure CozyDuke)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Use file system access controls to protect folders such as C:\Windows\System32. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1036/003
- Twitter ItsReallyNick Masquerading Update: https://twitter.com/ItsReallyNick/status/1055321652777619457
- Elastic Masquerade Ball: https://www.elastic.co/blog/how-hunt-masquerade-ball
- F-Secure CozyDuke: https://www.f-secure.com/documents/996508/1030745/CozyDuke
- LOLBAS Main Site: https://lolbas-project.github.io/
