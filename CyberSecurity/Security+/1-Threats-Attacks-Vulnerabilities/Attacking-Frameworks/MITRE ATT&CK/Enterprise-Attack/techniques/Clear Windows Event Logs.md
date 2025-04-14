---
alias: T1070.001
---

## T1070.001

Adversaries may clear Windows Event Logs to hide the activity of an intrusion. Windows Event Logs are a record of a computer's alerts and notifications. There are three system-defined sources of events: System, Application, and Security, with five event types: Error, Warning, Information, Success Audit, and Failure Audit.


With administrator privileges, the event logs can be cleared with the following utility commands:

* <code>wevtutil cl system</code>
* <code>wevtutil cl application</code>
* <code>wevtutil cl security</code>

These logs may also be cleared through other mechanisms, such as the event viewer GUI or [PowerShell](https://attack.mitre.org/techniques/T1059/001). For example, adversaries may use the PowerShell command <code>Remove-EventLog -LogName Security</code> to delete the Security EventLog and after reboot, disable future logging.  Note: events may still be generated and logged in the .evtx file between the time the command is run and the reboot.(Citation: disable_win_evt_logging)

Adversaries may also attempt to clear logs by directly deleting the stored log files within `C:\Windows\System32\winevt\logs\`.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Remote Data Storage\|M1029]] | Remote Data Storage | Automatically forward events to a log server or data repository to prevent conditions in which the adversary can locate and manipulate data on the local system. When possible, minimize time delay on event reporting to avoid prolonged storage on the local system. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Protect generated event files that are stored locally with proper permissions and authentication and limit opportunities for adversaries to increase privileges by preventing Privilege Escalation opportunities. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Obfuscate/encrypt event files locally and in transit to avoid giving feedback to an adversary. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1070/001
- disable_win_evt_logging: https://ptylu.github.io/content/report/report.html?report=25
- Microsoft Clear-EventLog: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog
- Microsoft EventLog.Clear: https://msdn.microsoft.com/library/system.diagnostics.eventlog.clear.aspx
- Microsoft wevtutil Oct 2017: https://docs.microsoft.com/windows-server/administration/windows-commands/wevtutil
