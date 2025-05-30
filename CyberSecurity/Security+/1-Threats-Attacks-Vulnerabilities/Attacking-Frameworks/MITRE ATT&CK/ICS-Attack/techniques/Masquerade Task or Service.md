---
alias: T1036.004
---

## T1036.004

Adversaries may attempt to manipulate the name of a task or service to make it appear legitimate or benign. Tasks/services executed by the Task Scheduler or systemd will typically be given a name and/or description.(Citation: TechNet Schtasks)(Citation: Systemd Service Units) Windows services will have a service name as well as a display name. Many benign tasks and services exist that have commonly associated names. Adversaries may give tasks or services names that are similar or identical to those of legitimate ones.

Tasks or services contain other fields, such as a description, that adversaries may attempt to make appear legitimate.(Citation: Palo Alto Shamoon Nov 2016)(Citation: Fysbis Dr Web Analysis)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows
- Linux
- macOS

### Permissions Required

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1036/004
- Fysbis Dr Web Analysis: https://vms.drweb.com/virus/?i=4276269
- Palo Alto Shamoon Nov 2016: http://researchcenter.paloaltonetworks.com/2016/11/unit42-shamoon-2-return-disttrack-wiper/
- Systemd Service Units: https://www.freedesktop.org/software/systemd/man/systemd.service.html
- TechNet Schtasks: https://technet.microsoft.com/en-us/library/bb490996.aspx
