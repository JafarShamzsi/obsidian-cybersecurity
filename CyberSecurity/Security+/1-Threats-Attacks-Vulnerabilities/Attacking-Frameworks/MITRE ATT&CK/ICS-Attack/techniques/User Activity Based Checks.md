---
alias: T1497.002
---

## T1497.002

Adversaries may employ various user activity checks to detect and avoid virtualization and analysis environments. This may include changing behaviors based on the results of checks for the presence of artifacts indicative of a virtual machine environment (VME) or sandbox. If the adversary detects a VME, they may alter their malware to disengage from the victim or conceal the core functions of the implant. They may also search for VME artifacts before dropping secondary or additional payloads. Adversaries may use the information learned from [Virtualization/Sandbox Evasion](https://attack.mitre.org/techniques/T1497) during automated discovery to shape follow-on behaviors.(Citation: Deloitte Environment Awareness)

Adversaries may search for user activity on the host based on variables such as the speed/frequency of mouse movements and clicks (Citation: Sans Virtual Jan 2016) , browser history, cache, bookmarks, or number of files in common directories such as home or the desktop. Other methods may rely on specific user interaction with the system before the malicious code is activated, such as waiting for a document to close before activating a macro (Citation: Unit 42 Sofacy Nov 2018) or waiting for a user to double click on an embedded image to activate.(Citation: FireEye FIN7 April 2017) 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1497/002
- Deloitte Environment Awareness: https://drive.google.com/file/d/1t0jn3xr4ff2fR30oQAUn_RsWSnMpOAQc
- Sans Virtual Jan 2016: https://www.sans.org/reading-room/whitepapers/forensics/detecting-malware-sandbox-evasion-techniques-36667
- Unit 42 Sofacy Nov 2018: https://unit42.paloaltonetworks.com/unit42-sofacy-continues-global-attacks-wheels-new-cannon-trojan/
- FireEye FIN7 April 2017: https://www.fireeye.com/blog/threat-research/2017/04/fin7-phishing-lnk.html
