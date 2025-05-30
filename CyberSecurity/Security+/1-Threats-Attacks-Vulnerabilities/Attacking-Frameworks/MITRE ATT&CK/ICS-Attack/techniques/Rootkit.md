---
alias: T1014
---

## T1014

Adversaries may use rootkits to hide the presence of programs, files, network connections, services, drivers, and other system components. Rootkits are programs that hide the existence of malware by intercepting/hooking and modifying operating system API calls that supply system information. (Citation: Symantec Windows Rootkits) 

Rootkits or rootkit enabling functionality may reside at the user or kernel level in the operating system or lower, to include a hypervisor, Master Boot Record, or [System Firmware](https://attack.mitre.org/techniques/T1542/001). (Citation: Wikipedia Rootkit) Rootkits have been seen for Windows, Linux, and Mac OS X systems. (Citation: CrowdStrike Linux Rootkit) (Citation: BlackHat Mac OSX Rootkit)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1014
- CrowdStrike Linux Rootkit: https://www.crowdstrike.com/blog/http-iframe-injecting-linux-rootkit/
- BlackHat Mac OSX Rootkit: http://www.blackhat.com/docs/asia-14/materials/Tsai/WP-Asia-14-Tsai-You-Cant-See-Me-A-Mac-OS-X-Rootkit-Uses-The-Tricks-You-Havent-Known-Yet.pdf
- Symantec Windows Rootkits: https://www.symantec.com/avcenter/reference/windows.rootkit.overview.pdf
- Wikipedia Rootkit: https://en.wikipedia.org/wiki/Rootkit
