---
alias: T1031
---

## T1031

Windows service configuration information, including the file path to the service's executable or recovery programs/commands, is stored in the Registry. Service configurations can be modified using utilities such as sc.exe and [Reg](https://attack.mitre.org/software/S0075).

Adversaries can modify an existing service to persist malware on a system by using system utilities or by using custom tools to interact with the Windows API. Use of existing services is a type of [Masquerading](https://attack.mitre.org/techniques/T1036) that may make detection analysis more challenging. Modifying existing services may interrupt their functionality or may enable services that are disabled or otherwise not commonly used.

Adversaries may also intentionally corrupt or kill services to execute malicious recovery programs/commands. (Citation: Twitter Service Recovery Nov 2017) (Citation: Microsoft Service Recovery Feb 2013)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows

### Permissions Required
- Administrator
- SYSTEM

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit privileges of user accounts and groups so that only authorized administrators can interact with service changes and service configurations. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Use auditing tools capable of detecting privilege and service abuse opportunities on systems within an enterprise and correct them. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1031
- capec: https://capec.mitre.org/data/definitions/551.html
- Twitter Service Recovery Nov 2017: https://twitter.com/r0wdy_/status/936365549553991680
- Microsoft Service Recovery Feb 2013: https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753662(v=ws.11)
- TechNet Autoruns: https://technet.microsoft.com/en-us/sysinternals/bb963902
