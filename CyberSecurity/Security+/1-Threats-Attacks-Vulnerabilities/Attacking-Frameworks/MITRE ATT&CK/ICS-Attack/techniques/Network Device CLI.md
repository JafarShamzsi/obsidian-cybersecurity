---
alias: T1059.008
---

## T1059.008

Adversaries may abuse scripting or built-in command line interpreters (CLI) on network devices to execute malicious command and payloads. The CLI is the primary means through which users and administrators interact with the device in order to view system information, modify device operations, or perform diagnostic and administrative functions. CLIs typically contain various permission levels required for different commands. 

Scripting interpreters automate tasks and extend functionality beyond the command set included in the network OS. The CLI and scripting interpreter are accessible through a direct console connection, or through remote means, such as telnet or [SSH](https://attack.mitre.org/techniques/T1021/004).

Adversaries can use the network CLI to change how network devices behave and operate. The CLI may be used to manipulate traffic flows to intercept or manipulate data, modify startup configuration parameters to load malicious system software, or to disable security features or logging to avoid detection.(Citation: Cisco Synful Knock Evolution)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)

### Platforms
- Network

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | TACACS+ can keep control over which commands administrators are permitted to use through the configuration of authentication and command authorization. (Citation: Cisco IOS Software Integrity Assurance - TACACS) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Use of Authentication, Authorization, and Accounting (AAA) systems will limit actions users can perform and provide a history of user actions to detect unauthorized use and abuse. Ensure least privilege principles are applied to user accounts and groups so that only authorized users can perform configuration changes. (Citation: Cisco IOS Software Integrity Assurance - AAA) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Use of Authentication, Authorization, and Accounting (AAA) systems will limit actions administrators can perform and provide a history of user actions to detect unauthorized use and abuse. TACACS+ can keep control over which commands administrators are permitted to use through the configuration of authentication and command authorization(Citation: Cisco IOS Software Integrity Assurance - AAA) (Citation: Cisco IOS Software Integrity Assurance - TACACS) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1059/008
- Cisco IOS Software Integrity Assurance - Command History: https://tools.cisco.com/security/center/resources/integrity_assurance.html#23
- Cisco Synful Knock Evolution: https://blogs.cisco.com/security/evolution-of-attacks-on-cisco-ios-devices
