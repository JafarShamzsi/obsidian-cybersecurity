---
alias: T1562.002
---

## T1562.002

Adversaries may disable Windows event logging to limit data that can be leveraged for detections and audits. Windows event logs record user and system activity such as login attempts, process creation, and much more.(Citation: Windows Log Events) This data is used by security tools and analysts to generate detections.

The EventLog service maintains event logs from various system components and applications.(Citation: EventLog_Core_Technologies) By default, the service automatically starts when a system powers on. An audit policy, maintained by the Local Security Policy (secpol.msc), defines which system events the EventLog service logs. Security audit policy settings can be changed by running secpol.msc, then navigating to <code>Security Settings\Local Policies\Audit Policy</code> for basic audit policy settings or <code>Security Settings\Advanced Audit Policy Configuration</code> for advanced audit policy settings.(Citation: Audit_Policy_Microsoft)(Citation: Advanced_sec_audit_policy_settings) <code>auditpol.exe</code> may also be used to set audit policies.(Citation: auditpol)

Adversaries may target system-wide logging or just that of a particular application. For example, the Windows EventLog service may be disabled using the <code>Set-Service -Name EventLog -Status Stopped</code> or <code>sc config eventlog start=disabled</code> commands (followed by manually stopping the service using <code>Stop-Service  -Name EventLog</code>).(Citation: Disable_Win_Event_Logging)(Citation: disable_win_evt_logging) Additionally, the service may be disabled by modifying the “Start” value in <code>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog</code> then restarting the system for the change to take effect.(Citation: disable_win_evt_logging)

There are several ways to disable the EventLog service via registry key modification. First, without Administrator privileges, adversaries may modify the "Start" value in the key <code>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Autologger\EventLog-Security</code>, then reboot the system to disable the Security EventLog.(Citation: winser19_file_overwrite_bug_twitter) Second, with Administrator privilege, adversaries may modify the same values in <code>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Autologger\EventLog-System</code> and <code>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Autologger\EventLog-Application</code> to disable the entire EventLog.(Citation: disable_win_evt_logging)

Additionally, adversaries may use <code>auditpol</code> and its sub-commands in a command prompt to disable auditing or clear the audit policy. To enable or disable a specified setting or audit category, adversaries may use the <code>/success</code> or <code>/failure</code> parameters. For example, <code>auditpol /set /category:”Account Logon” /success:disable /failure:disable</code> turns off auditing for the Account Logon category.(Citation: auditpol.exe_STRONTIC)(Citation: T1562.002_redcanaryco) To clear the audit policy, adversaries may run the following lines: <code>auditpol /clear /y</code> or <code>auditpol /remove /allusers</code>.(Citation: T1562.002_redcanaryco)

By disabling Windows event logging, adversaries can operate while leaving less evidence of a compromise behind.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Ensure proper user permissions are in place to prevent adversaries from disabling or interfering with logging. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Ensure proper process and file permissions are in place to prevent adversaries from disabling or interfering with logging or deleting or modifying .evtx logging files. Ensure .evtx files, which are located at <code>C:\Windows\system32\Winevt\Logs</code>(Citation: win_xml_evt_log), have the proper file permissions for limited, legitimate access and audit policies for detection.  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict Registry Permissions\|M1024]] | Restrict Registry Permissions | Ensure proper Registry permissions are in place to prevent adversaries from disabling or interfering logging. The addition of the MiniNT registry key disables Event Viewer.(Citation: def_ev_win_event_logging) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Consider periodic review of <code>auditpol</code> settings for Administrator accounts and perform dynamic baselining on SIEM(s) to investigate potential malicious activity. Also ensure that the EventLog service and its threads are properly running. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1562/002
- Disable_Win_Event_Logging: https://dmcxblue.gitbook.io/red-team-notes-2-0/red-team-techniques/defense-evasion/t1562-impair-defenses/disable-windows-event-logging
- def_ev_win_event_logging: https://www.hackingarticles.in/defense-evasion-windows-event-logging-t1562-002/
- EventLog_Core_Technologies: https://www.coretechnologies.com/blog/windows-services/eventlog/
- Audit_Policy_Microsoft: https://docs.microsoft.com/en-us/windows/security/threat-protection/security-policy-settings/audit-policy
- Windows Log Events: https://www.ultimatewindowssecurity.com/securitylog/encyclopedia/
- disable_win_evt_logging: https://ptylu.github.io/content/report/report.html?report=25
- auditpol: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/auditpol
- winser19_file_overwrite_bug_twitter: https://web.archive.org/web/20211107115646/https://twitter.com/klinix5/status/1457316029114327040
- T1562.002_redcanaryco: https://github.com/redcanaryco/atomic-red-team/blob/master/atomics/T1562.002/T1562.002.md
- Advanced_sec_audit_policy_settings: https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/advanced-security-audit-policy-settings
- auditpol.exe_STRONTIC: https://strontic.github.io/xcyclopedia/library/auditpol.exe-214E0EA1F7F7C27C82D23F183F9D23F1.html
- evt_log_tampering: https://svch0st.medium.com/event-log-tampering-part-1-disrupting-the-eventlog-service-8d4b7d67335c
