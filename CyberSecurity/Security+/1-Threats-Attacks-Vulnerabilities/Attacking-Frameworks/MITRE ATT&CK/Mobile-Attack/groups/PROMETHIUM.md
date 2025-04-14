---
alias: PROMETHIUM, StrongPity
---

## G0056

[PROMETHIUM](https://attack.mitre.org/groups/G0056) is an activity group focused on espionage that has been active since at least 2012. The group has conducted operations globally with a heavy emphasis on Turkish targets. [PROMETHIUM](https://attack.mitre.org/groups/G0056) has demonstrated similarity to another activity group called [NEODYMIUM](https://attack.mitre.org/groups/G0055) due to overlapping victim and campaign characteristics.(Citation: Microsoft NEODYMIUM Dec 2016)(Citation: Microsoft SIR Vol 21)(Citation: Talos Promethium June 2020)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Malicious File\|T1204.002]] | Malicious File | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has attempted to get users to execute compromised installation files for legitimate software including compression applications, security software, browsers, file recovery applications, and other tools and utilities.(Citation: Talos Promethium June 2020)(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Code Signing Certificates\|T1587.002]] | Code Signing Certificates | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has created self-signed certificates to sign malicious installers.(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Local Accounts\|T1078.003]] | Local Accounts | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has created admin accounts on a compromised host.(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Digital Certificates\|T1587.003]] | Digital Certificates | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has created self-signed digital certificates for use in HTTPS C2 traffic.(Citation: Talos Promethium June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Registry Run Keys ／ Startup Folder\|T1547.001]] | Registry Run Keys ／ Startup Folder | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has used Registry run keys to establish persistence.(Citation: Talos Promethium June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Windows Service\|T1543.003]] | Windows Service | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has created new services and modified existing services for persistence.(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Match Legitimate Name or Location\|T1036.005]] | Match Legitimate Name or Location | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has disguised malicious installer files by bundling them with legitimate software installers.(Citation: Talos Promethium June 2020)(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Masquerade Task or Service\|T1036.004]] | Masquerade Task or Service | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has named services to appear legitimate.(Citation: Talos Promethium June 2020)(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Code Signing\|T1553.002]] | Code Signing | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has signed code with self-signed certificates.(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Port Knocking\|T1205.001]] | Port Knocking | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has used a script that configures the knockd service and firewall to only accept C2 connections from systems that use a specified sequence of knock ports.(Citation: Bitdefender StrongPity June 2020) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Drive-by Compromise\|T1189]] | Drive-by Compromise | [PROMETHIUM](https://attack.mitre.org/groups/G0056) has used watering hole attacks to deliver malicious versions of legitimate installers.(Citation: Bitdefender StrongPity June 2020) |
