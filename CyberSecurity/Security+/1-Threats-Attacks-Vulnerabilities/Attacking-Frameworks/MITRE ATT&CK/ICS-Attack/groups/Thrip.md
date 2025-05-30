---
alias: Thrip
---

## G0076

[Thrip](https://attack.mitre.org/groups/G0076) is an espionage group that has targeted satellite communications, telecoms, and defense contractor companies in the U.S. and Southeast Asia. The group uses custom malware as well as "living off the land" techniques. (Citation: Symantec Thrip June 2018)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/PowerShell\|T1059.001]] | PowerShell | [Thrip](https://attack.mitre.org/groups/G0076) leveraged PowerShell to run commands to download payloads, traverse the compromised networks, and carry out reconnaissance.(Citation: Symantec Thrip June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Exfiltration Over Unencrypted Non-C2 Protocol\|T1048.003]] | Exfiltration Over Unencrypted Non-C2 Protocol | [Thrip](https://attack.mitre.org/groups/G0076) has used WinSCP to exfiltrate data from a targeted organization over FTP.(Citation: Symantec Thrip June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Remote Access Software\|T1219]] | Remote Access Software | [Thrip](https://attack.mitre.org/groups/G0076) used a cloud-based remote access software called LogMeIn for their attacks.(Citation: Symantec Thrip June 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Tool\|T1588.002]] | Tool | [Thrip](https://attack.mitre.org/groups/G0076) has obtained and used tools such as [Mimikatz](https://attack.mitre.org/software/S0002) and [PsExec](https://attack.mitre.org/software/S0029).(Citation: Symantec Thrip June 2018) |
