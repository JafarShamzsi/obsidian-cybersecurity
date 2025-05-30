---
alias: T1497
---

## T1497

Adversaries may employ various means to detect and avoid virtualization and analysis environments. This may include changing behaviors based on the results of checks for the presence of artifacts indicative of a virtual machine environment (VME) or sandbox. If the adversary detects a VME, they may alter their malware to disengage from the victim or conceal the core functions of the implant. They may also search for VME artifacts before dropping secondary or additional payloads. Adversaries may use the information learned from [Virtualization/Sandbox Evasion](https://attack.mitre.org/techniques/T1497) during automated discovery to shape follow-on behaviors.(Citation: Deloitte Environment Awareness)

Adversaries may use several methods to accomplish [Virtualization/Sandbox Evasion](https://attack.mitre.org/techniques/T1497) such as checking for security monitoring tools (e.g., Sysinternals, Wireshark, etc.) or other system artifacts associated with analysis or virtualization. Adversaries may also check for legitimate user activity to help determine if it is in an analysis environment. Additional methods include use of sleep timers or loops within malware code to avoid operating within a temporary sandbox.(Citation: Unit 42 Pirpi July 2015)




### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows
- macOS
- Linux

### Permissions Required

### Mitigations

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/System Checks\|T1497.001]] | System Checks |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Time Based Evasion\|T1497.003]] | Time Based Evasion |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/User Activity Based Checks\|T1497.002]] | User Activity Based Checks |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1497
- Deloitte Environment Awareness: https://drive.google.com/file/d/1t0jn3xr4ff2fR30oQAUn_RsWSnMpOAQc
- Unit 42 Pirpi July 2015: https://unit42.paloaltonetworks.com/ups-observations-on-cve-2015-3113-prior-zero-days-and-the-pirpi-payload/
