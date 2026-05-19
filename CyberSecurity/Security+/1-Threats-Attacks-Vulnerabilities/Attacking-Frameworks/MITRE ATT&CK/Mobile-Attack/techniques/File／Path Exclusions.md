---
alias: T1564.012
---

## T1564.012

Adversaries may attempt to hide their file-based artifacts by writing them to specific folders or file names excluded from antivirus (AV) scanning and other defensive capabilities. AV and other file-based scanners often include exclusions to optimize performance as well as ease installation and legitimate use of applications. These exclusions may be contextual (e.g., scans are only initiated in response to specific triggering events/alerts), but are also often hardcoded strings referencing specific folders and/or files assumed to be trusted and legitimate.(Citation: Microsoft File Folder Exclusions)

Adversaries may abuse these exclusions to hide their file-based artifacts. For example, rather than  tampering with tool settings to add a new exclusion (i.e., [Disable or Modify Tools](https://attack.mitre.org/techniques/T1562/001)), adversaries may drop their file-based payloads in default or otherwise well-known exclusions. Adversaries may also use [Security Software Discovery](https://attack.mitre.org/techniques/T1518/001) and other [Discovery](https://attack.mitre.org/tactics/TA0007)/[Reconnaissance](https://attack.mitre.org/tactics/TA0043) activities to both discover and verify existing exclusions in a victim environment.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Application Developer Guidance\|M1013]] | Application Developer Guidance | Application developers should consider limiting the requirements for custom or otherwise difficult to manage file/folder exclusions. Where possible, install applications to trusted system folder paths that are already protected by restricted file and directory permissions. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Antivirus／Antimalware\|M1049]] | Antivirus／Antimalware | Review and audit file/folder exclusions, and limit scope of exclusions to only what is required where possible.(Citation: Microsoft File Folder Exclusions) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1564/012
- Microsoft File Folder Exclusions: https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-contextual-file-folder-exclusions-microsoft-defender-antivirus
