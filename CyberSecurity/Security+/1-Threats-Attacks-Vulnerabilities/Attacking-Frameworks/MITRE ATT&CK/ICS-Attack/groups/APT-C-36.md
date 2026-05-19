---
alias: APT-C-36, Blind Eagle
---

## G0099

[APT-C-36](https://attack.mitre.org/groups/G0099) is a suspected South America espionage group that has been active since at least 2018. The group mainly targets Colombian government institutions as well as important corporations in the financial sector, petroleum industry, and professional manufacturing.(Citation: QiAnXin APT-C-36 Feb2019)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Malicious File\|T1204.002]] | Malicious File | [APT-C-36](https://attack.mitre.org/groups/G0099) has prompted victims to accept macros in order to execute the subsequent payload.(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Masquerade Task or Service\|T1036.004]] | Masquerade Task or Service | [APT-C-36](https://attack.mitre.org/groups/G0099) has disguised its scheduled tasks as those used by Google.(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Tool\|T1588.002]] | Tool | [APT-C-36](https://attack.mitre.org/groups/G0099) obtained and used a modified variant of [Imminent Monitor](https://attack.mitre.org/software/S0434).(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Obfuscated Files or Information\|T1027]] | Obfuscated Files or Information | [APT-C-36](https://attack.mitre.org/groups/G0099) has used ConfuserEx to obfuscate its variant of [Imminent Monitor](https://attack.mitre.org/software/S0434), compressed payload and RAT packages, and password protected encrypted email attachments to avoid detection.(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Scheduled Task\|T1053.005]] | Scheduled Task | [APT-C-36](https://attack.mitre.org/groups/G0099) has used a macro function to set scheduled tasks, disguised as those used by Google.(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | [APT-C-36](https://attack.mitre.org/groups/G0099) has downloaded binary data from a specified domain after the malicious document is opened.(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Visual Basic\|T1059.005]] | Visual Basic | [APT-C-36](https://attack.mitre.org/groups/G0099) has embedded a VBScript within a malicious Word document which is executed upon the document opening.(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Non-Standard Port\|T1571]] | Non-Standard Port | [APT-C-36](https://attack.mitre.org/groups/G0099) has used port 4050 for C2 communications.(Citation: QiAnXin APT-C-36 Feb2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Attachment\|T1566.001]] | Spearphishing Attachment | [APT-C-36](https://attack.mitre.org/groups/G0099) has used spearphishing emails with password protected RAR attachment to avoid being detected by the email gateway.(Citation: QiAnXin APT-C-36 Feb2019)  |
