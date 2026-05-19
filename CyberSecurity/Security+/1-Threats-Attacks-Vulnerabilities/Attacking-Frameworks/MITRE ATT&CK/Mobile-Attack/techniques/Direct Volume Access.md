---
alias: T1006
---

## T1006

Adversaries may directly access a volume to bypass file access controls and file system monitoring. Windows allows programs to have direct access to logical volumes. Programs with direct access may read and write files directly from the drive by analyzing file system data structures. This technique may bypass Windows file access controls as well as file system monitoring tools. (Citation: Hakobyan 2009)

Utilities, such as `NinjaCopy`, exist to perform these actions in PowerShell.(Citation: Github PowerSploit Ninjacopy) Adversaries may also use built-in or third-party utilities (such as `vssadmin`, `wbadmin`, and [esentutl](https://attack.mitre.org/software/S0404)) to create shadow copies or backups of data from system volumes.(Citation: LOLBAS Esentutl)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows
- Network

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | Some endpoint security solutions can be configured to block some types of behaviors related to efforts by an adversary to create backups, such as command execution or preventing API calls to backup related services. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Ensure only accounts required to configure and manage backups have the privileges to do so. Monitor these accounts for unauthorized backup activity. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1006
- Github PowerSploit Ninjacopy: https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Invoke-NinjaCopy.ps1
- Hakobyan 2009: http://www.codeproject.com/Articles/32169/FDump-Dumping-File-Sectors-Directly-from-Disk-usin
- LOLBAS Esentutl: https://lolbas-project.github.io/lolbas/Binaries/Esentutl/
