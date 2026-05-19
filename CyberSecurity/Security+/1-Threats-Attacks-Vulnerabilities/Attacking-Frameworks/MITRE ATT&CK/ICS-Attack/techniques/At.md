---
alias: T1053.002
---

## T1053.002

Adversaries may abuse the [at](https://attack.mitre.org/software/S0110) utility to perform task scheduling for initial or recurring execution of malicious code. The [at](https://attack.mitre.org/software/S0110) utility exists as an executable within Windows, Linux, and macOS for scheduling tasks at a specified time and date. Although deprecated in favor of [Scheduled Task](https://attack.mitre.org/techniques/T1053/005)'s [schtasks](https://attack.mitre.org/software/S0111) in Windows environments, using [at](https://attack.mitre.org/software/S0110) requires that the Task Scheduler service be running, and the user to be logged on as a member of the local Administrators group.

On Linux and macOS, [at](https://attack.mitre.org/software/S0110) may be invoked by the superuser as well as any users added to the <code>at.allow</code> file. If the <code>at.allow</code> file does not exist, the <code>at.deny</code> file is checked. Every username not listed in <code>at.deny</code> is allowed to invoke [at](https://attack.mitre.org/software/S0110). If the <code>at.deny</code> exists and is empty, global use of [at](https://attack.mitre.org/software/S0110) is permitted. If neither file exists (which is often the baseline) only the superuser is allowed to use [at](https://attack.mitre.org/software/S0110).(Citation: Linux at)

Adversaries may use [at](https://attack.mitre.org/software/S0110) to execute programs at system startup or on a scheduled basis for [Persistence](https://attack.mitre.org/tactics/TA0003). [at](https://attack.mitre.org/software/S0110) can also be abused to conduct remote [Execution](https://attack.mitre.org/tactics/TA0002) as part of [Lateral Movement](https://attack.mitre.org/tactics/TA0008) and/or to run a process under the context of a specified account (such as SYSTEM).

In Linux environments, adversaries may also abuse [at](https://attack.mitre.org/software/S0110) to break out of restricted environments by using a task to spawn an interactive system shell or to run system commands. Similarly, [at](https://attack.mitre.org/software/S0110) may also be used for [Privilege Escalation](https://attack.mitre.org/tactics/TA0004) if the binary is allowed to run as superuser via <code>sudo</code>.(Citation: GTFObins at)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Windows
- Linux
- macOS

### Permissions Required
- Administrator
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Operating System Configuration\|M1028]] | Operating System Configuration | Configure settings for scheduled tasks to force tasks to run under the context of the authenticated account instead of allowing them to run as SYSTEM. The associated Registry key is located at <code>HKLM\SYSTEM\CurrentControlSet\Control\Lsa\SubmitControl</code>. The setting can be configured through GPO: Computer Configuration > [Policies] > Windows Settings > Security Settings > Local Policies > Security Options: Domain Controller: Allow server operators to schedule tasks, set to disabled. (Citation: TechNet Server Operator Scheduled Task)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit privileges of user accounts and remediate Privilege Escalation vectors so only authorized administrators can create scheduled tasks on remote systems. In Linux environments, users account-level access to <code>[at](https://attack.mitre.org/software/S0110)</code> can be managed using <code>at.allow</code> and <code>at.deny</code> files. Users listed in the at.allow are enabled to schedule actions using at, whereas users listed in at.deny file disabled from the utility. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Configure the Increase Scheduling Priority option to only allow the Administrators group the rights to schedule a priority process. This can be configured through GPO: Computer Configuration > [Policies] > Windows Settings > Security Settings > Local Policies > User Rights Assignment: Increase scheduling priority. (Citation: TechNet Scheduling Priority) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Toolkits like the PowerSploit framework contain PowerUp modules that can be used to explore systems for permission weaknesses in scheduled tasks that could be used to escalate privileges. (Citation: Powersploit) Windows operating system also creates a registry key specifically associated with the creation of a scheduled task on the destination host at: Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tree\At1. (Citation: Secureworks - AT.exe Scheduled Task) In Linux and macOS environments, scheduled tasks using <code>[at](https://attack.mitre.org/software/S0110)</code> can be audited locally, or through centrally collected logging, using syslog, or auditd events from the host. (Citation: Kifarunix - Task Scheduling in Linux) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1053/002
- rowland linux at 2019: https://www.linkedin.com/pulse/getting-attacker-ip-address-from-malicious-linux-job-craig-rowland/
- GTFObins at: https://gtfobins.github.io/gtfobins/at/
- Linux at: https://man7.org/linux/man-pages/man1/at.1p.html
- Twitter Leoloobeek Scheduled Task: https://twitter.com/leoloobeek/status/939248813465853953
- Microsoft Scheduled Task Events Win10: https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/audit-other-object-access-events
- TechNet Scheduled Task Events: https://technet.microsoft.com/library/dd315590.aspx
- TechNet Autoruns: https://technet.microsoft.com/en-us/sysinternals/bb963902
- TechNet Forum Scheduled Task Operational Setting: https://social.technet.microsoft.com/Forums/en-US/e5bca729-52e7-4fcb-ba12-3225c564674c/scheduled-tasks-history-retention-settings?forum=winserver8gen
