---
alias: Group5
---

## G0043

[Group5](https://attack.mitre.org/groups/G0043) is a threat group with a suspected Iranian nexus, though this attribution is not definite. The group has targeted individuals connected to the Syrian opposition via spearphishing and watering holes, normally using Syrian and Iranian themes. [Group5](https://attack.mitre.org/groups/G0043) has used two commonly available remote access tools (RATs), [njRAT](https://attack.mitre.org/software/S0385) and [NanoCore](https://attack.mitre.org/software/S0336), as well as an Android RAT, DroidJack. (Citation: Citizen Lab Group5)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Keylogging\|T1056.001]] | Keylogging | Malware used by [Group5](https://attack.mitre.org/groups/G0043) is capable of capturing keystrokes.(Citation: Citizen Lab Group5) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Screen Capture\|T1113]] | Screen Capture | Malware used by [Group5](https://attack.mitre.org/groups/G0043) is capable of watching the victim's screen.(Citation: Citizen Lab Group5) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/File Deletion\|T1070.004]] | File Deletion | Malware used by [Group5](https://attack.mitre.org/groups/G0043) is capable of remotely deleting files from victims.(Citation: Citizen Lab Group5) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Encrypted／Encoded File\|T1027.013]] | Encrypted／Encoded File | [Group5](https://attack.mitre.org/groups/G0043) disguised its malicious binaries with several layers of obfuscation, including encrypting the files.(Citation: Citizen Lab Group5) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Uncommonly Used Port\|T1065]] | Uncommonly Used Port | [Group5](https://attack.mitre.org/groups/G0043) C2 servers communicated with malware over TCP 8081, 8282, and 8083.(Citation: Citizen Lab Group5) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Software Packing\|T1045]] | Software Packing | [Group5](https://attack.mitre.org/groups/G0043) packed an executable by base64 encoding the PE file and breaking it up into numerous lines. |
