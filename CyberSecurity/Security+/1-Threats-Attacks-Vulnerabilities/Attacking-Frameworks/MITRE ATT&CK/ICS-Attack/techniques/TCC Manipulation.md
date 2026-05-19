---
alias: T1548.006
---

## T1548.006

Adversaries can manipulate or abuse the Transparency, Consent, & Control (TCC) service or database to execute malicious applications with elevated permissions. TCC is a Privacy & Security macOS control mechanism used to determine if the running process has permission to access the data or services protected by TCC, such as screen sharing, camera, microphone, or Full Disk Access (FDA).

When an application requests to access data or a service protected by TCC, the TCC daemon (`tccd`) checks the TCC database, located at `/Library/Application Support/com.apple.TCC/TCC.db` (and `~/` equivalent), for existing permissions. If permissions do not exist, then the user is prompted to grant permission. Once permissions are granted, the database stores the application's permissions and will not prompt the user again unless reset. For example, when a web browser requests permissions to the user's webcam, once granted the web browser may not explicitly prompt the user again.(Citation: welivesecurity TCC)

Adversaries may manipulate the TCC database or otherwise abuse the TCC service to execute malicious content. This can be done in various ways, including using privileged system applications to execute malicious payloads or manipulating the database to grant their application TCC permissions. 

For example, adversaries can use Finder, which has FDA permissions by default, to execute malicious [AppleScript](https://attack.mitre.org/techniques/T1059/002) while preventing a user prompt. For a system without System Integrity Protection (SIP) enabled, adversaries have also manipulated the operating system to load an adversary controlled TCC database using environment variables and [Launchctl](https://attack.mitre.org/techniques/T1569/001).(Citation: TCC macOS bypass)(Citation: TCC Database)

Adversaries may also opt to instead inject code (e.g., [Process Injection](https://attack.mitre.org/techniques/T1055)) into targeted applications with the desired TCC permissions.



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | When using an MDM, ensure the permissions granted are specific to the requirements of the binary. Full Disk Access should be restricted to only necessary binaries in alignment with policy.  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Remove unnecessary users from the local administrator group on systems. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Routinely check applications using Automation under Security & Privacy System Preferences. To reset permissions, user's can utilize the `tccutil reset` command. When using Mobile Device Management (MDM), review the list of enabled or disabled applications in the `MDMOverrides.plist` which overrides the TCC database.(Citation: TCC macOS bypass) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Update Software\|M1051]] | Update Software | Routinely update software. Where possible, ensure systems are macOS Sierra+ and SIP is enabled.(Citation: welivesecurity TCC) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1548/006
- welivesecurity TCC: https://www.welivesecurity.com/2022/07/19/i-see-what-you-did-there-look-cloudmensis-macos-spyware/
- TCC Database: https://interpressecurity.com/resources/return-of-the-macos-tcc/
- TCC macOS bypass: https://www.sentinelone.com/labs/bypassing-macos-tcc-user-privacy-protections-by-accident-and-design/
