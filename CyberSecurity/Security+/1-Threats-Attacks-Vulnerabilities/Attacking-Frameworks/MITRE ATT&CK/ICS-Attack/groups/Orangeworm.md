---
alias: Orangeworm
---

## G0071

[Orangeworm](https://attack.mitre.org/groups/G0071) is a group that has targeted organizations in the healthcare sector in the United States, Europe, and Asia since at least 2015, likely for the purpose of corporate espionage.(Citation: Symantec Orangeworm April 2018) Reverse engineering of [Kwampirs](https://attack.mitre.org/software/S0236), directly associated with [Orangeworm](https://attack.mitre.org/groups/G0071) activity, indicates significant functional and development overlaps with [Shamoon](https://attack.mitre.org/software/S0140).(Citation: Cylera Kwampirs 2022)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Web Protocols\|T1071.001]] | Web Protocols | [Orangeworm](https://attack.mitre.org/groups/G0071) has used HTTP for C2.(Citation: Symantec Orangeworm IOCs April 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/SMB／Windows Admin Shares\|T1021.002]] | SMB／Windows Admin Shares | [Orangeworm](https://attack.mitre.org/groups/G0071) has copied its backdoor across open network shares, including ADMIN$, C$WINDOWS, D$WINDOWS, and E$WINDOWS.(Citation: Symantec Orangeworm April 2018) |
