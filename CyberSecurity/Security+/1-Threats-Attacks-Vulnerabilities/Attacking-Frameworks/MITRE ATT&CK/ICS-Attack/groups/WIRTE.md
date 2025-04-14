---
alias: WIRTE
---

## G0090

[WIRTE](https://attack.mitre.org/groups/G0090) is a threat group that has been active since at least August 2018. [WIRTE](https://attack.mitre.org/groups/G0090) has targeted government, diplomatic, financial, military, legal, and technology organizations in the Middle East and Europe.(Citation: Lab52 WIRTE Apr 2019)(Citation: Kaspersky WIRTE November 2021)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/PowerShell\|T1059.001]] | PowerShell | [WIRTE](https://attack.mitre.org/groups/G0090) has used PowerShell for script execution.(Citation: Lab52 WIRTE Apr 2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Non-Standard Port\|T1571]] | Non-Standard Port | [WIRTE](https://attack.mitre.org/groups/G0090) has used HTTPS over ports 2083 and 2087 for C2.(Citation: Kaspersky WIRTE November 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Visual Basic\|T1059.005]] | Visual Basic | [WIRTE](https://attack.mitre.org/groups/G0090) has used VBScript  in its operations.(Citation: Lab52 WIRTE Apr 2019)	 |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Malicious File\|T1204.002]] | Malicious File | [WIRTE](https://attack.mitre.org/groups/G0090) has attempted to lure users into opening malicious MS Word and Excel files to execute malicious payloads.(Citation: Kaspersky WIRTE November 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Deobfuscate／Decode Files or Information\|T1140]] | Deobfuscate／Decode Files or Information | [WIRTE](https://attack.mitre.org/groups/G0090) has used Base64 to decode malicious VBS script.(Citation: Lab52 WIRTE Apr 2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Attachment\|T1566.001]] | Spearphishing Attachment | [WIRTE](https://attack.mitre.org/groups/G0090) has sent emails to intended victims with malicious MS Word and Excel attachments.(Citation: Kaspersky WIRTE November 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Match Legitimate Name or Location\|T1036.005]] | Match Legitimate Name or Location | [WIRTE](https://attack.mitre.org/groups/G0090) has named a first stage dropper `Kaspersky Update Agent` in order to appear legitimate.(Citation: Kaspersky WIRTE November 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Tool\|T1588.002]] | Tool | [WIRTE](https://attack.mitre.org/groups/G0090) has obtained and used [Empire](https://attack.mitre.org/software/S0363) for post-exploitation activities.(Citation: Lab52 WIRTE Apr 2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Web Protocols\|T1071.001]] | Web Protocols | [WIRTE](https://attack.mitre.org/groups/G0090) has used HTTP for network communication.(Citation: Lab52 WIRTE Apr 2019)	 |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Regsvr32\|T1218.010]] | Regsvr32 | [WIRTE](https://attack.mitre.org/groups/G0090) has used `regsvr32.exe` to trigger the execution of a malicious script.(Citation: Lab52 WIRTE Apr 2019) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | [WIRTE](https://attack.mitre.org/groups/G0090) has downloaded PowerShell code from the C2 server to be executed.(Citation: Lab52 WIRTE Apr 2019) |
