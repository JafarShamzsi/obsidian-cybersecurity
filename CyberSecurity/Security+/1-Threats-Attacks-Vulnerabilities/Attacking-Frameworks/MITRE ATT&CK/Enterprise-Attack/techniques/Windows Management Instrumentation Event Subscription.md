---
alias: T1084
---

## T1084

Windows Management Instrumentation (WMI) can be used to install event filters, providers, consumers, and bindings that execute code when a defined event occurs. Adversaries may use the capabilities of WMI to subscribe to an event and execute arbitrary code when that event occurs, providing persistence on a system. Adversaries may attempt to evade detection of this technique by compiling WMI scripts into Windows Management Object (MOF) files (.mof extension). (Citation: Dell WMI Persistence) Examples of events that may be subscribed to are the wall clock time or the computer's uptime. (Citation: Kazanciyan 2014) Several threat groups have reportedly used this technique to maintain persistence. (Citation: Mandiant M-Trends 2015)


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
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | By default, only administrators are allowed to connect remotely using WMI; restrict other users that are allowed to connect, or disallow all users from connecting remotely to WMI. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Prevent credential overlap across systems of administrator and privileged accounts. (Citation: FireEye WMI 2015) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1084
- Dell WMI Persistence: https://www.secureworks.com/blog/wmi-persistence
- Kazanciyan 2014: https://www.defcon.org/images/defcon-22/dc-22-presentations/Kazanciyan-Hastings/DEFCON-22-Ryan-Kazanciyan-Matt-Hastings-Investigating-Powershell-Attacks.pdf
- Mandiant M-Trends 2015: https://www2.fireeye.com/rs/fireye/images/rpt-m-trends-2015.pdf
- TechNet Autoruns: https://technet.microsoft.com/en-us/sysinternals/bb963902
- Medium Detecting WMI Persistence: https://medium.com/threatpunter/detecting-removing-wmi-persistence-60ccbb7dff96
