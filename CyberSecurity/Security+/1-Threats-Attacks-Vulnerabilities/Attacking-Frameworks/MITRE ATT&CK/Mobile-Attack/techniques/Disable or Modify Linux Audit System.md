---
alias: T1562.012
---

## T1562.012

Adversaries may disable or modify the Linux audit system to hide malicious activity and avoid detection. Linux admins use the Linux Audit system to track security-relevant information on a system. The Linux Audit system operates at the kernel-level and maintains event logs on application and system activity such as process, network, file, and login events based on pre-configured rules.

Often referred to as `auditd`, this is the name of the daemon used to write events to disk and is governed by the parameters set in the `audit.conf` configuration file. Two primary ways to configure the log generation rules are through the command line `auditctl` utility and the file `/etc/audit/audit.rules`,  containing a sequence of `auditctl` commands loaded at boot time.(Citation: Red Hat System Auditing)(Citation: IzyKnows auditd threat detection 2022)

With root privileges, adversaries may be able to ensure their activity is not logged through disabling the Audit system service, editing the configuration/rule files, or by hooking the Audit system library functions. Using the command line, adversaries can disable the Audit system service through killing processes associated with `auditd` daemon or use `systemctl` to stop the Audit service. Adversaries can also hook Audit system functions to disable logging or modify the rules contained in the `/etc/audit/audit.rules` or `audit.conf` files to ignore malicious activity.(Citation: Trustwave Honeypot SkidMap 2023)(Citation: ESET Ebury Feb 2014)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | An adversary must already have root level access on the local system to make full use of this technique; be sure to restrict users and accounts to the least privileges they require. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Routinely check account role permissions to ensure only expected users and roles have permission to modify logging settings.<br /><br />To ensure Audit rules can not be modified at runtime, add the `auditctl -e 2` as the last command in the audit.rules files. Once started, any attempt to change the configuration in this mode will be audited and denied. The configuration can only be changed by rebooting the machine. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1562/012
- IzyKnows auditd threat detection 2022: https://izyknows.medium.com/linux-auditd-for-threat-detection-d06c8b941505
- Red Hat System Auditing: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/chap-system_auditing
- ESET Ebury Feb 2014: https://www.welivesecurity.com/2014/02/21/an-in-depth-analysis-of-linuxebury/
- Trustwave Honeypot SkidMap 2023: https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/honeypot-recon-new-variant-of-skidmap-targeting-redis/
