---
alias: T1070.002
---

## T1070.002

Adversaries may clear system logs to hide evidence of an intrusion. macOS and Linux both keep track of system or user-initiated actions via system logs. The majority of native system logging is stored under the <code>/var/log/</code> directory. Subfolders in this directory categorize logs by their related functions, such as:(Citation: Linux Logs)

* <code>/var/log/messages:</code>: General and system-related messages
* <code>/var/log/secure</code> or <code>/var/log/auth.log</code>: Authentication logs
* <code>/var/log/utmp</code> or <code>/var/log/wtmp</code>: Login records
* <code>/var/log/kern.log</code>: Kernel logs
* <code>/var/log/cron.log</code>: Crond logs
* <code>/var/log/maillog</code>: Mail server logs
* <code>/var/log/httpd/</code>: Web server access and error logs



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Remote Data Storage\|M1029]] | Remote Data Storage | Automatically forward events to a log server or data repository to prevent conditions in which the adversary can locate and manipulate data on the local system. When possible, minimize time delay on event reporting to avoid prolonged storage on the local system. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Protect generated event files that are stored locally with proper permissions and authentication and limit opportunities for adversaries to increase privileges by preventing Privilege Escalation opportunities. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Obfuscate/encrypt event files locally and in transit to avoid giving feedback to an adversary. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1070/002
- Linux Logs: https://www.eurovps.com/blog/important-linux-log-files-you-must-be-monitoring/
