---
alias: Equation
---

## G0020

[Equation](https://attack.mitre.org/groups/G0020) is a sophisticated threat group that employs multiple remote access tools. The group is known to use zero-day exploits and has developed the capability to overwrite the firmware of hard disk drives. (Citation: Kaspersky Equation QA)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Hidden File System\|T1564.005]] | Hidden File System | [Equation](https://attack.mitre.org/groups/G0020) has used an encrypted virtual file system stored in the Windows Registry.(Citation: Kaspersky Equation QA) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Peripheral Device Discovery\|T1120]] | Peripheral Device Discovery | [Equation](https://attack.mitre.org/groups/G0020) has used tools with the functionality to search for specific information about the attached hard drive that could be used to identify and overwrite the firmware.(Citation: Kaspersky Equation QA) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Environmental Keying\|T1480.001]] | Environmental Keying | [Equation](https://attack.mitre.org/groups/G0020) has been observed utilizing environmental keying in payload delivery.(Citation: Kaspersky Gauss Whitepaper)(Citation: Kaspersky Equation QA) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Component Firmware\|T1542.002]] | Component Firmware | [Equation](https://attack.mitre.org/groups/G0020) is known to have the capability to overwrite the firmware on hard drives from some manufacturers.(Citation: Kaspersky Equation QA)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Component Firmware\|T1109]] | Component Firmware | [Equation](https://attack.mitre.org/groups/G0020) is known to have the capability to overwrite the firmware on hard drives from some manufacturers.(Citation: Kaspersky Equation QA) |
