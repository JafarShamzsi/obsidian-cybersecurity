---
alias: T1053.001
---

## T1053.001

Adversaries may abuse the [at](https://attack.mitre.org/software/S0110) utility to perform task scheduling for initial, recurring, or future execution of malicious code. The [at](https://attack.mitre.org/software/S0110) command within Linux operating systems enables administrators to schedule tasks.(Citation: Kifarunix - Task Scheduling in Linux)

An adversary may use [at](https://attack.mitre.org/software/S0110) in Linux environments to execute programs at system startup or on a scheduled basis for persistence. [at](https://attack.mitre.org/software/S0110) can also be abused to conduct remote Execution as part of Lateral Movement and or to run a process under the context of a specified account.

Adversaries may also abuse [at](https://attack.mitre.org/software/S0110) to break out of restricted environments by using a task to spawn an interactive system shell or to run system commands. Similarly, [at](https://attack.mitre.org/software/S0110) may also be used for [Privilege Escalation](https://attack.mitre.org/tactics/TA0004) if the binary is allowed to run as superuser via <code>sudo</code>.(Citation: GTFObins at)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Users account-level access to <code>[at](https://attack.mitre.org/software/S0110)</code> can be managed using <code>/etc/at.allow</code> and <code>/etc/at.deny</code> files. Users listed in the at.allow are enabled to schedule actions using at, whereas users listed in at.deny file disabled from the utility. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Scheduled tasks using <code>[at](https://attack.mitre.org/software/S0110)</code> can be audited locally, or through centrally collected logging, using syslog, or auditd events from the host. (Citation: Kifarunix - Task Scheduling in Linux) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1053/001
- rowland linux at 2019: https://www.linkedin.com/pulse/getting-attacker-ip-address-from-malicious-linux-job-craig-rowland/
- GTFObins at: https://gtfobins.github.io/gtfobins/at/
- Kifarunix - Task Scheduling in Linux: https://kifarunix.com/scheduling-tasks-using-at-command-in-linux/
