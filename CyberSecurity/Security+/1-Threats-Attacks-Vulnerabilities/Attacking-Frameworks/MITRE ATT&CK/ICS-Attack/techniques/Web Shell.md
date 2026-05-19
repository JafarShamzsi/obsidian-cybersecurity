---
alias: T1100
---

## T1100

A Web shell is a Web script that is placed on an openly accessible Web server to allow an adversary to use the Web server as a gateway into a network. A Web shell may provide a set of functions to execute or a command-line interface on the system that hosts the Web server. In addition to a server-side script, a Web shell may have a client interface program that is used to talk to the Web server (see, for example, China Chopper Web shell client). (Citation: Lee 2013)

Web shells may serve as [Redundant Access](https://attack.mitre.org/techniques/T1108) or as a persistence mechanism in case an adversary's primary access methods are detected and removed.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Linux
- Windows
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Audit account and group permissions to ensure that accounts used to manage servers do not overlap with accounts and permissions of users in the internal network that could be acquired through Credential Access and used to log into the Web server and plant a Web shell or pivot from the Web server into the internal network. (Citation: US-CERT Alert TA15-314A Web Shells) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Update Software\|M1051]] | Update Software | Ensure that externally facing Web servers are patched regularly to prevent adversary access through [Exploitation for Privilege Escalation](https://attack.mitre.org/techniques/T1068) to gain remote code access or through file inclusion weaknesses that may allow adversaries to upload files or scripts that are automatically served as Web pages. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1100
- capec: https://capec.mitre.org/data/definitions/650.html
- Lee 2013: https://www.fireeye.com/blog/threat-research/2013/08/breaking-down-the-china-chopper-web-shell-part-i.html
- US-CERT Alert TA15-314A Web Shells: https://www.us-cert.gov/ncas/alerts/TA15-314A
