---
alias: DarkHydrus
---

## G0079

[DarkHydrus](https://attack.mitre.org/groups/G0079) is a threat group that has targeted government agencies and educational institutions in the Middle East since at least 2016. The group heavily leverages open-source tools and custom payloads for carrying out attacks. (Citation: Unit 42 DarkHydrus July 2018) (Citation: Unit 42 Playbook Dec 2017)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Malicious File\|T1204.002]] | Malicious File | [DarkHydrus](https://attack.mitre.org/groups/G0079) has sent malware that required users to hit the enable button in Microsoft Excel to allow an .iqy file to be downloaded.(Citation: Unit 42 DarkHydrus July 2018)(Citation: Unit 42 Playbook Dec 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Forced Authentication\|T1187]] | Forced Authentication | [DarkHydrus](https://attack.mitre.org/groups/G0079) used [Template Injection](https://attack.mitre.org/techniques/T1221) to launch an authentication window for users to enter their credentials.(Citation: Unit 42 Phishery Aug 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Hidden Window\|T1564.003]] | Hidden Window | [DarkHydrus](https://attack.mitre.org/groups/G0079) has used <code>-WindowStyle Hidden</code> to conceal [PowerShell](https://attack.mitre.org/techniques/T1059/001) windows. (Citation: Unit 42 DarkHydrus July 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/PowerShell\|T1059.001]] | PowerShell | [DarkHydrus](https://attack.mitre.org/groups/G0079) leveraged PowerShell to download and execute additional scripts for execution.(Citation: Unit 42 DarkHydrus July 2018)(Citation: Unit 42 Playbook Dec 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Spearphishing Attachment\|T1566.001]] | Spearphishing Attachment | [DarkHydrus](https://attack.mitre.org/groups/G0079) has sent spearphishing emails with password-protected RAR archives containing malicious Excel Web Query files (.iqy). The group has also sent spearphishing emails that contained malicious Microsoft Office documents that use the “attachedTemplate” technique to load a template from a remote server.(Citation: Unit 42 DarkHydrus July 2018)(Citation: Unit 42 Phishery Aug 2018)(Citation: Unit 42 Playbook Dec 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Template Injection\|T1221]] | Template Injection | [DarkHydrus](https://attack.mitre.org/groups/G0079) used an open-source tool, Phishery, to inject malicious remote template URLs into Microsoft Word documents and then sent them to victims to enable [Forced Authentication](https://attack.mitre.org/techniques/T1187).(Citation: Unit 42 Phishery Aug 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Tool\|T1588.002]] | Tool | [DarkHydrus](https://attack.mitre.org/groups/G0079) has obtained and used tools such as [Mimikatz](https://attack.mitre.org/software/S0002), [Empire](https://attack.mitre.org/software/S0363), and [Cobalt Strike](https://attack.mitre.org/software/S0154).(Citation: Unit 42 DarkHydrus July 2018) |
