---
alias: Putter Panda, APT2, MSUpdater
---

## G0024

[Putter Panda](https://attack.mitre.org/groups/G0024) is a Chinese threat group that has been attributed to Unit 61486 of the 12th Bureau of the PLA’s 3rd General Staff Department (GSD). (Citation: CrowdStrike Putter Panda)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Registry Run Keys ／ Startup Folder\|T1547.001]] | Registry Run Keys ／ Startup Folder | A dropper used by [Putter Panda](https://attack.mitre.org/groups/G0024) installs itself into the ASEP Registry key <code>HKCU\Software\Microsoft\Windows\CurrentVersion\Run</code> with a value named McUpdate.(Citation: CrowdStrike Putter Panda) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Disable or Modify Tools\|T1562.001]] | Disable or Modify Tools | Malware used by [Putter Panda](https://attack.mitre.org/groups/G0024) attempts to terminate processes corresponding to two components of Sophos Anti-Virus (SAVAdminService.exe and SavService.exe).(Citation: CrowdStrike Putter Panda) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Dynamic-link Library Injection\|T1055.001]] | Dynamic-link Library Injection | An executable dropped onto victims by [Putter Panda](https://attack.mitre.org/groups/G0024) aims to inject the specified DLL into a process that would normally be accessing the network, including Outlook Express (msinm.exe), Outlook (outlook.exe), Internet Explorer (iexplore.exe), and Firefox (firefox.exe).(Citation: CrowdStrike Putter Panda) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Encrypted／Encoded File\|T1027.013]] | Encrypted／Encoded File | Droppers used by [Putter Panda](https://attack.mitre.org/groups/G0024) use RC4 or a 16-byte XOR key consisting of the bytes 0xA0 – 0xAF to obfuscate payloads.(Citation: CrowdStrike Putter Panda) |
