---
alias: APT18, TG-0416, Dynamite Panda, Threat Group-0416
---

## G0026

[APT18](https://attack.mitre.org/groups/G0026) is a threat group that has operated since at least 2009 and has targeted a range of industries, including technology, manufacturing, human rights groups, government, and medical. (Citation: Dell Lateral Movement)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Valid Accounts\|T1078]] | Valid Accounts | [APT18](https://attack.mitre.org/groups/G0026) actors leverage legitimate credentials to log into external remote services.(Citation: RSA2017 Detect and Respond Adair) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Encrypted／Encoded File\|T1027.013]] | Encrypted／Encoded File | [APT18](https://attack.mitre.org/groups/G0026) obfuscates strings in the payload.(Citation: PaloAlto DNS Requests May 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/External Remote Services\|T1133]] | External Remote Services | [APT18](https://attack.mitre.org/groups/G0026) actors leverage legitimate credentials to log into external remote services.(Citation: RSA2017 Detect and Respond Adair) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/File Deletion\|T1070.004]] | File Deletion | [APT18](https://attack.mitre.org/groups/G0026) actors deleted tools and batch files from victim systems.(Citation: Dell Lateral Movement) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/At\|T1053.002]] | At | [APT18](https://attack.mitre.org/groups/G0026) actors used the native [at](https://attack.mitre.org/software/S0110) Windows task scheduler tool to use scheduled tasks for execution on a victim network.(Citation: Dell Lateral Movement) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | [APT18](https://attack.mitre.org/groups/G0026) can upload a file to the victim’s machine.(Citation: PaloAlto DNS Requests May 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/DNS\|T1071.004]] | DNS | [APT18](https://attack.mitre.org/groups/G0026) uses DNS for C2 communications.(Citation: PaloAlto DNS Requests May 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/System Information Discovery\|T1082]] | System Information Discovery | [APT18](https://attack.mitre.org/groups/G0026) can collect system information from the victim’s machine.(Citation: PaloAlto DNS Requests May 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Web Protocols\|T1071.001]] | Web Protocols | [APT18](https://attack.mitre.org/groups/G0026) uses HTTP for C2 communications.(Citation: PaloAlto DNS Requests May 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/File and Directory Discovery\|T1083]] | File and Directory Discovery | [APT18](https://attack.mitre.org/groups/G0026) can list files information for specific directories.(Citation: PaloAlto DNS Requests May 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Windows Command Shell\|T1059.003]] | Windows Command Shell | [APT18](https://attack.mitre.org/groups/G0026) uses cmd.exe to execute commands on the victim’s machine.(Citation: PaloAlto DNS Requests May 2016)(Citation: Anomali Evasive Maneuvers July 2015) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Registry Run Keys ／ Startup Folder\|T1547.001]] | Registry Run Keys ／ Startup Folder | [APT18](https://attack.mitre.org/groups/G0026) establishes persistence via the <code>HKCU\Software\Microsoft\Windows\CurrentVersion\Run</code> key.(Citation: Anomali Evasive Maneuvers July 2015)(Citation: PaloAlto DNS Requests May 2016) |
