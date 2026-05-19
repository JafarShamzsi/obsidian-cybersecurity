---
alias: T1218.007
---

## T1218.007

Adversaries may abuse msiexec.exe to proxy execution of malicious payloads. Msiexec.exe is the command-line utility for the Windows Installer and is thus commonly associated with executing installation packages (.msi).(Citation: Microsoft msiexec) The Msiexec.exe binary may also be digitally signed by Microsoft.

Adversaries may abuse msiexec.exe to launch local or network accessible MSI files. Msiexec.exe can also execute DLLs.(Citation: LOLBAS Msiexec)(Citation: TrendMicro Msiexec Feb 2018) Since it may be signed and native on Windows systems, msiexec.exe can be used to bypass application control solutions that do not account for its potential abuse. Msiexec.exe execution may also be elevated to SYSTEM privileges if the <code>AlwaysInstallElevated</code> policy is enabled.(Citation: Microsoft AlwaysInstallElevated 2018)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Restrict execution of Msiexec.exe to privileged accounts or groups that need to use it to lessen the opportunities for malicious usage. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Consider disabling the <code>AlwaysInstallElevated</code> policy to prevent elevated execution of Windows Installer packages.(Citation: Microsoft AlwaysInstallElevated 2018) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1218/007
- TrendMicro Msiexec Feb 2018: https://blog.trendmicro.com/trendlabs-security-intelligence/attack-using-windows-installer-msiexec-exe-leads-lokibot/
- LOLBAS Msiexec: https://lolbas-project.github.io/lolbas/Binaries/Msiexec/
- Microsoft msiexec: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/msiexec
- Microsoft AlwaysInstallElevated 2018: https://docs.microsoft.com/en-us/windows/win32/msi/alwaysinstallelevated
