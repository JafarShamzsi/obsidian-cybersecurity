---
alias: Sharpshooter
---

## G0104

Operation [Sharpshooter](https://attack.mitre.org/groups/G0104) is the name of a cyber espionage campaign discovered in October 2018 targeting nuclear, defense, energy, and financial companies. Though overlaps between this adversary and [Lazarus Group](https://attack.mitre.org/groups/G0032) have been noted, definitive links have not been established.(Citation: McAfee Sharpshooter December 2018)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | [Sharpshooter](https://attack.mitre.org/groups/G0104) downloaded additional payloads after a target was infected with a first-stage downloader.(Citation: McAfee Sharpshooter December 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Malicious File\|T1204.002]] | Malicious File | [Sharpshooter](https://attack.mitre.org/groups/G0104) has sent malicious DOC and PDF files to targets so that they can be opened by a user.(Citation: McAfee Sharpshooter December 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Visual Basic\|T1059.005]] | Visual Basic | [Sharpshooter](https://attack.mitre.org/groups/G0104)'s first-stage downloader was a VBA macro.(Citation: McAfee Sharpshooter December 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Native API\|T1106]] | Native API | [Sharpshooter](https://attack.mitre.org/groups/G0104)'s first-stage downloader resolved various Windows libraries and APIs, including LoadLibraryA(), GetProcAddress(), and CreateProcessA().(Citation: McAfee Sharpshooter December 2018)	 |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Dynamic Data Exchange\|T1559.002]] | Dynamic Data Exchange | [Sharpshooter](https://attack.mitre.org/groups/G0104) has sent malicious Word OLE documents to victims.(Citation: McAfee Sharpshooter December 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Process Injection\|T1055]] | Process Injection | [Sharpshooter](https://attack.mitre.org/groups/G0104) has leveraged embedded shellcode to inject a downloader into the memory of Word.(Citation: McAfee Sharpshooter December 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Attachment\|T1566.001]] | Spearphishing Attachment | [Sharpshooter](https://attack.mitre.org/groups/G0104) has sent malicious attachments via emails to targets.(Citation: McAfee Sharpshooter December 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Registry Run Keys ／ Startup Folder\|T1547.001]] | Registry Run Keys ／ Startup Folder | [Sharpshooter](https://attack.mitre.org/groups/G0104)'s first-stage downloader installed [Rising Sun](https://attack.mitre.org/software/S0448) to the startup folder <code>%Startup%\mssync.exe</code>.(Citation: McAfee Sharpshooter December 2018)	 |
