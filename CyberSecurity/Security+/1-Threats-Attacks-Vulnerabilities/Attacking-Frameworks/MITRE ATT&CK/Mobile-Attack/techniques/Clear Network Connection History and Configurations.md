---
alias: T1070.007
---

## T1070.007

Adversaries may clear or remove evidence of malicious network connections in order to clean up traces of their operations. Configuration settings as well as various artifacts that highlight connection history may be created on a system and/or in application logs from behaviors that require network connections, such as [Remote Services](https://attack.mitre.org/techniques/T1021) or [External Remote Services](https://attack.mitre.org/techniques/T1133). Defenders may use these artifacts to monitor or otherwise analyze network connections created by adversaries.

Network connection history may be stored in various locations. For example, RDP connection history may be stored in Windows Registry values under (Citation: Microsoft RDP Removal):

* <code>HKEY_CURRENT_USER\Software\Microsoft\Terminal Server Client\Default</code>
* <code>HKEY_CURRENT_USER\Software\Microsoft\Terminal Server Client\Servers</code>

Windows may also store information about recent RDP connections in files such as <code>C:\Users\\%username%\Documents\Default.rdp</code> and `C:\Users\%username%\AppData\Local\Microsoft\Terminal
Server Client\Cache\`.(Citation: Moran RDPieces) Similarly, macOS and Linux hosts may store information highlighting connection history in system logs (such as those stored in `/Library/Logs` and/or `/var/log/`).(Citation: Apple Culprit Access)(Citation: FreeDesktop Journal)(Citation: Apple Unified Log Analysis Remote Login and Screen Sharing)

Malicious network connections may also require changes to third-party applications or network configuration settings, such as [Disable or Modify System Firewall](https://attack.mitre.org/techniques/T1562/004) or tampering to enable [Proxy](https://attack.mitre.org/techniques/T1090). Adversaries may delete or modify this data to conceal indicators and/or impede defensive analysis.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows
- Network

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Remote Data Storage\|M1029]] | Remote Data Storage | Automatically forward events to a log server or data repository to prevent conditions in which the adversary can locate and manipulate data on the local system. When possible, minimize time delay on event reporting to avoid prolonged storage on the local system. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict Registry Permissions\|M1024]] | Restrict Registry Permissions | Protect generated event files and logs that are stored locally with proper permissions and authentication and limit opportunities for adversaries to increase privileges by preventing Privilege Escalation opportunities. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1070/007
- FreeDesktop Journal: https://www.freedesktop.org/software/systemd/man/systemd-journald.service.html
- Microsoft RDP Removal: https://docs.microsoft.com/troubleshoot/windows-server/remote/remove-entries-from-remote-desktop-connection-computer
- Moran RDPieces: https://www.osdfcon.org/presentations/2020/Brian-Moran_Putting-Together-the-RDPieces.pdf
- Apple Culprit Access: https://discussions.apple.com/thread/3991574
- Apple Unified Log Analysis Remote Login and Screen Sharing: https://sarah-edwards-xzkc.squarespace.com/blog/2020/4/30/analysis-of-apple-unified-logs-quarantine-edition-entry-6-working-from-home-remote-logins
