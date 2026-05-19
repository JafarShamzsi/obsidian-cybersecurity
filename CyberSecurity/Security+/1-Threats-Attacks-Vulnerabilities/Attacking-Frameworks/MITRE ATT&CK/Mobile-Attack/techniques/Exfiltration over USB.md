---
alias: T1052.001
---

## T1052.001

Adversaries may attempt to exfiltrate data over a USB connected physical device. In certain circumstances, such as an air-gapped network compromise, exfiltration could occur via a USB device introduced by a user. The USB device could be used as the final exfiltration point or to hop between otherwise disconnected systems.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Exfiltration]] (TA0010)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Limit Hardware Installation\|M1034]] | Limit Hardware Installation | Limit the use of USB devices and removable media within a network. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Data Loss Prevention\|M1057]] | Data Loss Prevention | Data loss prevention can detect and block sensitive data being copied to USB devices. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Disable Autorun if it is unnecessary. (Citation: Microsoft Disable Autorun) Disallow or restrict removable media at an organizational policy level if they are not required for business operations. (Citation: TechNet Removable Media Control) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1052/001
