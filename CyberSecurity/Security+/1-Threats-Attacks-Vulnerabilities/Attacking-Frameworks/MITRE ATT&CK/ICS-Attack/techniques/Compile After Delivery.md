---
alias: T1500
---

## T1500

Adversaries may attempt to make payloads difficult to discover and analyze by delivering files to victims as uncompiled code. Similar to [Obfuscated Files or Information](https://attack.mitre.org/techniques/T1027), text-based source code files may subvert analysis and scrutiny from protections targeting executables/binaries. These payloads will need to be compiled before execution; typically via native utilities such as csc.exe or GCC/MinGW.(Citation: ClearSky MuddyWater Nov 2018)

Source code payloads may also be encrypted, encoded, and/or embedded within other files, such as those delivered as a [Spearphishing Attachment](https://attack.mitre.org/techniques/T1193). Payloads may also be delivered in formats unrecognizable and inherently benign to the native OS (ex: EXEs on macOS/Linux) before later being (re)compiled into a proper executable binary with a bundled compiler and execution framework.(Citation: TrendMicro WindowsAppMac)



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required
- User

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1500
- ClearSky MuddyWater Nov 2018: https://www.clearskysec.com/wp-content/uploads/2018/11/MuddyWater-Operations-in-Lebanon-and-Oman.pdf
- TrendMicro WindowsAppMac: https://blog.trendmicro.com/trendlabs-security-intelligence/windows-app-runs-on-mac-downloads-info-stealer-and-adware/
