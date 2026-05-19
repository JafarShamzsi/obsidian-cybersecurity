---
alias: T1074.001
---

## T1074.001

Adversaries may stage collected data in a central location or directory on the local system prior to Exfiltration. Data may be kept in separate files or combined into one file through techniques such as [Archive Collected Data](https://attack.mitre.org/techniques/T1560). Interactive command shells may be used, and common functionality within [cmd](https://attack.mitre.org/software/S0106) and bash may be used to copy data into a staging location.

Adversaries may also stage collected data in various available formats/locations of a system, including local storage databases/repositories or the Windows Registry.(Citation: Prevailion DarkWatchman 2021)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Collection]] (TA0009)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1074/001
- Prevailion DarkWatchman 2021: https://www.prevailion.com/darkwatchman-new-fileless-techniques/
