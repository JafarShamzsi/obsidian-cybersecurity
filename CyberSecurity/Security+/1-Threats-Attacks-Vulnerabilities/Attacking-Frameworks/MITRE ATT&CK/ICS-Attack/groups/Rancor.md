---
alias: Rancor
---

## G0075

[Rancor](https://attack.mitre.org/groups/G0075) is a threat group that has led targeted campaigns against the South East Asia region. [Rancor](https://attack.mitre.org/groups/G0075) uses politically-motivated lures to entice victims to open malicious documents. (Citation: Rancor Unit42 June 2018)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Web Protocols\|T1071.001]] | Web Protocols | [Rancor](https://attack.mitre.org/groups/G0075) has used HTTP for C2.(Citation: Rancor Unit42 June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Visual Basic\|T1059.005]] | Visual Basic | [Rancor](https://attack.mitre.org/groups/G0075) has used VBS scripts as well as embedded macros for execution.(Citation: Rancor Unit42 June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Malicious File\|T1204.002]] | Malicious File | [Rancor](https://attack.mitre.org/groups/G0075) attempted to get users to click on an embedded macro within a Microsoft Office Excel document to launch their malware.(Citation: Rancor Unit42 June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Scheduled Task\|T1053.005]] | Scheduled Task | [Rancor](https://attack.mitre.org/groups/G0075) launched a scheduled task to gain persistence using the <code>schtasks /create /sc</code> command.(Citation: Rancor Unit42 June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | [Rancor](https://attack.mitre.org/groups/G0075) has downloaded additional malware, including by using [certutil](https://attack.mitre.org/software/S0160).(Citation: Rancor Unit42 June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Msiexec\|T1218.007]] | Msiexec | [Rancor](https://attack.mitre.org/groups/G0075) has used <code>msiexec</code> to download and execute malicious installer files over HTTP.(Citation: Rancor Unit42 June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Windows Management Instrumentation Event Subscription\|T1546.003]] | Windows Management Instrumentation Event Subscription | [Rancor](https://attack.mitre.org/groups/G0075) has complied VBScript-generated MOF files into WMI event subscriptions for persistence.(Citation: Rancor WMI) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Windows Command Shell\|T1059.003]] | Windows Command Shell | [Rancor](https://attack.mitre.org/groups/G0075) has used cmd.exe to execute commmands.(Citation: Rancor Unit42 June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Attachment\|T1566.001]] | Spearphishing Attachment | [Rancor](https://attack.mitre.org/groups/G0075) has attached a malicious document to an email to gain initial access.(Citation: Rancor Unit42 June 2018) |
