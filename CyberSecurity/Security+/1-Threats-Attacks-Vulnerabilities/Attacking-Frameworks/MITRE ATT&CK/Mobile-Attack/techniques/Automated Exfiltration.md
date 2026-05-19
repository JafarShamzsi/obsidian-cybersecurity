---
alias: T1020
---

## T1020

Adversaries may exfiltrate data, such as sensitive documents, through the use of automated processing after being gathered during Collection.(Citation: ESET Gamaredon June 2020) 

When automated exfiltration is used, other exfiltration techniques likely apply as well to transfer the information out of the network, such as [Exfiltration Over C2 Channel](https://attack.mitre.org/techniques/T1041) and [Exfiltration Over Alternative Protocol](https://attack.mitre.org/techniques/T1048).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Exfiltration]] (TA0010)

### Platforms
- Linux
- macOS
- Windows
- Network

### Permissions Required

### Mitigations

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Traffic Duplication\|T1020.001]] | Traffic Duplication |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1020
- ESET Gamaredon June 2020: https://www.welivesecurity.com/2020/06/11/gamaredon-group-grows-its-game/
