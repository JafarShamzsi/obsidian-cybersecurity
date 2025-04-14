---
alias: T1028
---

## T1028

Windows Remote Management (WinRM) is the name of both a Windows service and a protocol that allows a user to interact with a remote system (e.g., run an executable, modify the Registry, modify services). (Citation: Microsoft WinRM) It may be called with the <code>winrm</code> command or by any number of programs such as PowerShell. (Citation: Jacobsen 2014)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Lateral Movement]] (TA0008)

### Platforms
- Windows

### Permissions Required
- User
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Network Segmentation\|M1030]] | Network Segmentation | If the service is necessary, lock down critical enclaves with separate WinRM infrastructure and follow WinRM best practices on use of host firewalls to restrict WinRM access to allow communication only to/from specific devices. (Citation: NSA Spotting) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | If the service is necessary, lock down critical enclaves with separate WinRM accounts and permissions. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Disable the WinRM service. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1028
- capec: https://capec.mitre.org/data/definitions/555.html
- Microsoft WinRM: http://msdn.microsoft.com/en-us/library/aa384426
- Jacobsen 2014: https://www.slideshare.net/kieranjacobsen/lateral-movement-with-power-shell-2
- Medium Detecting Lateral Movement: https://medium.com/threatpunter/detecting-lateral-movement-using-sysmon-and-splunk-318d3be141bc
