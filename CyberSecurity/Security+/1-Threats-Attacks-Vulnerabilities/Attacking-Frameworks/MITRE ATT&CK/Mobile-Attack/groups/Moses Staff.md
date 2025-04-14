---
alias: Moses Staff, DEV-0500, Marigold Sandstorm
---

## G1009

[Moses Staff](https://attack.mitre.org/groups/G1009) is a suspected Iranian threat group that has primarily targeted Israeli companies since at least September 2021. [Moses Staff](https://attack.mitre.org/groups/G1009) openly stated their motivation in attacking Israeli companies is to cause damage by leaking stolen sensitive data and encrypting the victim's networks without a ransom demand.(Citation: Checkpoint MosesStaff Nov 2021) 

Security researchers assess [Moses Staff](https://attack.mitre.org/groups/G1009) is politically motivated, and has targeted government, finance, travel, energy, manufacturing, and utility companies outside of Israel as well, including those in Italy, India, Germany, Chile, Turkey, the UAE, and the US.(Citation: Cybereason StrifeWater Feb 2022)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/SMB／Windows Admin Shares\|T1021.002]] | SMB／Windows Admin Shares | [Moses Staff](https://attack.mitre.org/groups/G1009) has used batch scripts that can enable SMB on a compromised host.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/System Network Configuration Discovery\|T1016]] | System Network Configuration Discovery | [Moses Staff](https://attack.mitre.org/groups/G1009) has collected the domain name of a compromised network.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Local Account\|T1087.001]] | Local Account | [Moses Staff](https://attack.mitre.org/groups/G1009) has collected the administrator username from a compromised host.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/System Information Discovery\|T1082]] | System Information Discovery | [Moses Staff](https://attack.mitre.org/groups/G1009) collected information about the infected host, including the machine names and OS architecture.(Citation: Checkpoint MosesStaff Nov 2021)<br /> |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Disable or Modify System Firewall\|T1562.004]] | Disable or Modify System Firewall | [Moses Staff](https://attack.mitre.org/groups/G1009) has used batch scripts that can disable the Windows firewall on specific remote machines.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Tool\|T1588.002]] | Tool | [Moses Staff](https://attack.mitre.org/groups/G1009) has used the commercial tool DiskCryptor.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Web Shell\|T1505.003]] | Web Shell | [Moses Staff](https://attack.mitre.org/groups/G1009) has dropped a web shell onto a compromised system.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Malware\|T1587.001]] | Malware | [Moses Staff](https://attack.mitre.org/groups/G1009) has built malware, such as [DCSrv](https://attack.mitre.org/software/S1033) and [PyDCrypt](https://attack.mitre.org/software/S1032), for targeting victims' machines.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Code Signing\|T1553.002]] | Code Signing | [Moses Staff](https://attack.mitre.org/groups/G1009) has used signed drivers from an open source tool called DiskCryptor to evade detection.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Encrypted／Encoded File\|T1027.013]] | Encrypted／Encoded File | [Moses Staff](https://attack.mitre.org/groups/G1009) has used obfuscated web shells in their operations.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | [Moses Staff](https://attack.mitre.org/groups/G1009) has downloaded and installed web shells to following path <code>C:\inetpub\wwwroot\aspnet_client\system_web\IISpool.aspx</code>.(Citation: Checkpoint MosesStaff Nov 2021) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Exploit Public-Facing Application\|T1190]] | Exploit Public-Facing Application | [Moses Staff](https://attack.mitre.org/groups/G1009) has exploited known vulnerabilities in public-facing infrastructure such as Microsoft Exchange Servers.(Citation: Checkpoint MosesStaff Nov 2021) |
