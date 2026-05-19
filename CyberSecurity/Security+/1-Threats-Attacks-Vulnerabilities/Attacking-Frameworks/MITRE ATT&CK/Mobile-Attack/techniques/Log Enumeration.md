---
alias: T1654
---

## T1654

Adversaries may enumerate system and service logs to find useful data. These logs may highlight various types of valuable insights for an adversary, such as user authentication records ([Account Discovery](https://attack.mitre.org/techniques/T1087)), security or vulnerable software ([Software Discovery](https://attack.mitre.org/techniques/T1518)), or hosts within a compromised network ([Remote System Discovery](https://attack.mitre.org/techniques/T1018)).

Host binaries may be leveraged to collect system logs. Examples include using `wevtutil.exe` or [PowerShell](https://attack.mitre.org/techniques/T1059/001) on Windows to access and/or export security event information.(Citation: WithSecure Lazarus-NoPineapple Threat Intel Report 2023)(Citation: Cadet Blizzard emerges as novel threat actor) In cloud environments, adversaries may leverage utilities such as the Azure VM Agent’s `CollectGuestLogs.exe` to collect security logs from cloud hosted infrastructure.(Citation: SIM Swapping and Abuse of the Microsoft Azure Serial Console)

Adversaries may also target centralized logging infrastructure such as SIEMs. Logs may also be bulk exported and sent to adversary-controlled infrastructure for offline analysis.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Linux
- macOS
- Windows
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit the ability to access and export sensitive logs to privileged accounts where possible. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1654
- SIM Swapping and Abuse of the Microsoft Azure Serial Console: https://www.mandiant.com/resources/blog/sim-swapping-abuse-azure-serial
- Cadet Blizzard emerges as novel threat actor: https://www.microsoft.com/en-us/security/blog/2023/06/14/cadet-blizzard-emerges-as-a-novel-and-distinct-russian-threat-actor/
- WithSecure Lazarus-NoPineapple Threat Intel Report 2023: https://labs.withsecure.com/content/dam/labs/docs/WithSecure-Lazarus-No-Pineapple-Threat-Intelligence-Report-2023.pdf
