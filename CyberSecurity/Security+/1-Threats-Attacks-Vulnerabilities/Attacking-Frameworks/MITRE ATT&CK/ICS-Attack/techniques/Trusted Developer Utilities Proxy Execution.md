---
alias: T1127
---

## T1127

Adversaries may take advantage of trusted developer utilities to proxy execution of malicious payloads. There are many utilities used for software development related tasks that can be used to execute code in various forms to assist in development, debugging, and reverse engineering.(Citation: engima0x3 DNX Bypass)(Citation: engima0x3 RCSI Bypass)(Citation: Exploit Monday WinDbg)(Citation: LOLBAS Tracker) These utilities may often be signed with legitimate certificates that allow them to execute on a system and proxy execution of malicious code through a trusted process that effectively bypasses application control solutions.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Certain developer utilities should be blocked or restricted if not required. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Specific developer utilities may not be necessary within a given environment and should be removed if not used. |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/MSBuild\|T1127.001]] | MSBuild |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1127
- Exploit Monday WinDbg: http://www.exploit-monday.com/2016/08/windbg-cdb-shellcode-runner.html
- LOLBAS Tracker: https://lolbas-project.github.io/lolbas/OtherMSBinaries/Tracker/
- engima0x3 RCSI Bypass: https://enigma0x3.net/2016/11/21/bypassing-application-whitelisting-by-using-rcsi-exe/
- engima0x3 DNX Bypass: https://enigma0x3.net/2016/11/17/bypassing-application-whitelisting-by-using-dnx-exe/
