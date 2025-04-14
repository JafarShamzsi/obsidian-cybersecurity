---
alias: T1564.011
---

## T1564.011

Adversaries may evade defensive mechanisms by executing commands that hide from process interrupt signals. Many operating systems use signals to deliver messages to control process behavior. Command interpreters often include specific commands/flags that ignore errors and other hangups, such as when the user of the active session logs off.(Citation: Linux Signal Man)  These interrupt signals may also be used by defensive tools and/or analysts to pause or terminate specified running processes. 

Adversaries may invoke processes using `nohup`, [PowerShell](https://attack.mitre.org/techniques/T1059/001) `-ErrorAction SilentlyContinue`, or similar commands that may be immune to hangups.(Citation: nohup Linux Man)(Citation: Microsoft PowerShell SilentlyContinue) This may enable malicious commands and malware to continue execution through system events that would otherwise terminate its execution, such as users logging off or the termination of its C2 network connection.

Hiding from process interrupt signals may allow malware to continue execution, but unlike [Trap](https://attack.mitre.org/techniques/T1546/005) this does not establish [Persistence](https://attack.mitre.org/tactics/TA0003) since the process will not be re-invoked once actually terminated.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1564/011
- Linux Signal Man: https://man7.org/linux/man-pages/man7/signal.7.html
- nohup Linux Man: https://linux.die.net/man/1/nohup
- Microsoft PowerShell SilentlyContinue: https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-7.3#debugpreference
