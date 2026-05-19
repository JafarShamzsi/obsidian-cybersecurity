---
alias: Metador
---

## G1013

[Metador](https://attack.mitre.org/groups/G1013) is a suspected cyber espionage group that was first reported in September 2022. [Metador](https://attack.mitre.org/groups/G1013) has targeted a limited number of telecommunication companies, internet service providers, and universities in the Middle East and Africa. Security researchers named the group [Metador](https://attack.mitre.org/groups/G1013) based on the "I am meta" string in one of the group's malware samples and the expectation of Spanish-language responses from C2 servers.(Citation: SentinelLabs Metador Sept 2022)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Web Protocols\|T1071.001]] | Web Protocols | [Metador](https://attack.mitre.org/groups/G1013) has used HTTP for C2.(Citation: SentinelLabs Metador Sept 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Windows Command Shell\|T1059.003]] | Windows Command Shell | [Metador](https://attack.mitre.org/groups/G1013) has used the Windows command line to execute commands.(Citation: SentinelLabs Metador Sept 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Malware\|T1588.001]] | Malware | [Metador](https://attack.mitre.org/groups/G1013) has used unique malware in their operations, including [metaMain](https://attack.mitre.org/software/S1059) and [Mafalda](https://attack.mitre.org/software/S1060).(Citation: SentinelLabs Metador Sept 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Windows Management Instrumentation Event Subscription\|T1546.003]] | Windows Management Instrumentation Event Subscription | [Metador](https://attack.mitre.org/groups/G1013) has established persistence through the use of a WMI event subscription combined with unusual living-off-the-land binaries such as `cdb.exe`.(Citation: SentinelLabs Metador Sept 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Encrypted／Encoded File\|T1027.013]] | Encrypted／Encoded File | [Metador](https://attack.mitre.org/groups/G1013) has encrypted their payloads.(Citation: SentinelLabs Metador Sept 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/File Deletion\|T1070.004]] | File Deletion | [Metador](https://attack.mitre.org/groups/G1013) has quickly deleted `cbd.exe` from a compromised host following the successful deployment of their malware.(Citation: SentinelLabs Metador Sept 2022)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Non-Application Layer Protocol\|T1095]] | Non-Application Layer Protocol | [Metador](https://attack.mitre.org/groups/G1013) has used TCP for C2.(Citation: SentinelLabs Metador Sept 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Tool\|T1588.002]] | Tool | [Metador](https://attack.mitre.org/groups/G1013) has used Microsoft's Console Debugger in some of their operations.(Citation: SentinelLabs Metador Sept 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | [Metador](https://attack.mitre.org/groups/G1013) has downloaded tools and malware onto a compromised system.(Citation: SentinelLabs Metador Sept 2022) |
