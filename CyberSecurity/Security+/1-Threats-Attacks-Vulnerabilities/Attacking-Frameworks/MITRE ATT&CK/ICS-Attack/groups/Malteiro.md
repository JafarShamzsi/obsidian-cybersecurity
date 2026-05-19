---
alias: Malteiro
---

## G1026

[Malteiro](https://attack.mitre.org/groups/G1026) is a financially motivated criminal group that is likely based in Brazil and has been active since at least November 2019. The group operates and distributes the [Mispadu](https://attack.mitre.org/software/S1122)  banking trojan via a Malware-as-a-Service (MaaS) business model. [Malteiro](https://attack.mitre.org/groups/G1026) mainly targets victims throughout Latin America (particularly Mexico) and Europe (particularly Spain and Portugal).(Citation: SCILabs Malteiro 2021)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Malicious File\|T1204.002]] | Malicious File | [Malteiro](https://attack.mitre.org/groups/G1026) has relied on users to execute .zip file attachments containing malicious URLs.(Citation: SCILabs Malteiro 2021)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Credentials from Web Browsers\|T1555.003]] | Credentials from Web Browsers | [Malteiro](https://attack.mitre.org/groups/G1026) has stolen credentials stored in the victim’s browsers via software tool NirSoft WebBrowserPassView.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Dynamic-link Library Injection\|T1055.001]] | Dynamic-link Library Injection | [Malteiro](https://attack.mitre.org/groups/G1026) has injected [Mispadu](https://attack.mitre.org/software/S1122)’s DLL into a process.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Financial Theft\|T1657]] | Financial Theft | [Malteiro](https://attack.mitre.org/groups/G1026) targets organizations in a wide variety of sectors via the use of [Mispadu](https://attack.mitre.org/software/S1122) banking trojan with the goal of financial theft.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/System Information Discovery\|T1082]] | System Information Discovery | [Malteiro](https://attack.mitre.org/groups/G1026) collects the machine information, system architecture, the OS version, computer name, and Windows product name.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Visual Basic\|T1059.005]] | Visual Basic | [Malteiro](https://attack.mitre.org/groups/G1026) has utilized a dropper containing malicious VBS scripts.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Encrypted／Encoded File\|T1027.013]] | Encrypted／Encoded File | [Malteiro](https://attack.mitre.org/groups/G1026) has used scripts encoded in Base64 certificates to distribute malware to victims.(Citation: SCILabs Malteiro Threat Overlap 2023) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Security Software Discovery\|T1518.001]] | Security Software Discovery | [Malteiro](https://attack.mitre.org/groups/G1026) collects the installed antivirus on the victim machine.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Attachment\|T1566.001]] | Spearphishing Attachment | [Malteiro](https://attack.mitre.org/groups/G1026) has sent spearphishing emails containing malicious .zip files.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Credentials from Password Stores\|T1555]] | Credentials from Password Stores | [Malteiro](https://attack.mitre.org/groups/G1026) has obtained credentials from mail clients via NirSoft MailPassView.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Deobfuscate／Decode Files or Information\|T1140]] | Deobfuscate／Decode Files or Information | [Malteiro](https://attack.mitre.org/groups/G1026) has the ability to deobfuscate downloaded files prior to execution.(Citation: SCILabs Malteiro 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/System Language Discovery\|T1614.001]] | System Language Discovery | [Malteiro](https://attack.mitre.org/groups/G1026) will terminate [Mispadu](https://attack.mitre.org/software/S1122)'s infection process if the language of the victim machine is not Spanish or Portuguese.(Citation: SCILabs Malteiro 2021) |
