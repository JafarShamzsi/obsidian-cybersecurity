---
alias: T1543.002
---

## T1543.002

Adversaries may create or modify systemd services to repeatedly execute malicious payloads as part of persistence. Systemd is a system and service manager commonly used for managing background daemon processes (also known as services) and other system resources.(Citation: Linux man-pages: systemd January 2014) Systemd is the default initialization (init) system on many Linux distributions replacing legacy init systems, including SysVinit and Upstart, while remaining backwards compatible.  

Systemd utilizes unit configuration files with the `.service` file extension to encode information about a service's process. By default, system level unit files are stored in the `/systemd/system` directory of the root owned directories (`/`). User level unit files are stored in the `/systemd/user` directories of the user owned directories (`$HOME`).(Citation: lambert systemd 2022) 

Inside the `.service` unit files, the following directives are used to execute commands:(Citation: freedesktop systemd.service)  

* `ExecStart`, `ExecStartPre`, and `ExecStartPost` directives execute when a service is started manually by `systemctl` or on system start if the service is set to automatically start.
* `ExecReload` directive executes when a service restarts. 
* `ExecStop`, `ExecStopPre`, and `ExecStopPost` directives execute when a service is stopped.  

Adversaries have created new service files, altered the commands a `.service` file’s directive executes, and modified the user directive a `.service` file executes as, which could result in privilege escalation. Adversaries may also place symbolic links in these directories, enabling systemd to find these payloads regardless of where they reside on the filesystem.(Citation: Anomali Rocke March 2019)(Citation: airwalk backdoor unix systems)(Citation: Rapid7 Service Persistence 22JUNE2016) 

The .service file’s User directive can be used to run service as a specific user, which could result in privilege escalation based on specific user/group permissions. 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Linux

### Permissions Required
- User
- root

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Limit Software Installation\|M1033]] | Limit Software Installation | Restrict software installation to trusted repositories only and be cautious of orphaned software packages. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit user access to system utilities such as `systemctl` to only users who have a legitimate need. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Restrict read/write access to systemd unit files to only select privileged users who have a legitimate need to manage system services. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | The creation and modification of systemd service unit files is generally reserved for administrators such as the Linux root user and other users with superuser privileges.  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1543/002
- airwalk backdoor unix systems: http://www.ouah.org/backdoors.html
- Anomali Rocke March 2019: https://www.anomali.com/blog/rocke-evolves-its-arsenal-with-a-new-malware-family-written-in-golang
- freedesktop systemd.service: https://www.freedesktop.org/software/systemd/man/systemd.service.html
- Linux man-pages: systemd January 2014: http://man7.org/linux/man-pages/man1/systemd.1.html
- Berba hunting linux systemd: https://pberba.github.io/security/2022/01/30/linux-threat-hunting-for-persistence-systemd-timers-cron/
- Rapid7 Service Persistence 22JUNE2016: https://www.rapid7.com/db/modules/exploit/linux/local/service_persistence
- lambert systemd 2022: https://redcanary.com/blog/attck-t1501-understanding-systemd-service-persistence/
