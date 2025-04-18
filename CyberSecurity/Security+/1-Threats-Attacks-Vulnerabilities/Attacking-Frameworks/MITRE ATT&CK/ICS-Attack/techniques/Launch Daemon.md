---
alias: T1160
---

## T1160

Per Apple’s developer documentation, when macOS and OS X boot up, launchd is run to finish system initialization. This process loads the parameters for each launch-on-demand system-level daemon from the property list (plist) files found in <code>/System/Library/LaunchDaemons</code> and <code>/Library/LaunchDaemons</code> (Citation: AppleDocs Launch Agent Daemons). These LaunchDaemons have property list files which point to the executables that will be launched (Citation: Methods of Mac Malware Persistence).
 
Adversaries may install a new launch daemon that can be configured to execute at startup by using launchd or launchctl to load a plist into the appropriate directories (Citation: OSX Malware Detection). The daemon name may be disguised by using a name from a related operating system or benign software  (Citation: WireLurker). Launch Daemons may be created with administrator privileges, but are executed under root privileges, so an adversary may also use a service to escalate privileges from administrator to root.
 
The plist file permissions must be root:wheel, but the script or program that it points to has no such requirement. So, it is possible for poor configurations to allow an adversary to modify a current Launch Daemon’s executable and gain persistence or Privilege Escalation.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- macOS

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit privileges of user accounts and remediate Privilege Escalation vectors so only authorized administrators can create new Launch Daemons. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1160
- AppleDocs Launch Agent Daemons: https://developer.apple.com/library/content/documentation/MacOSX/Conceptual/BPSystemStartup/Chapters/CreatingLaunchdJobs.html
- Methods of Mac Malware Persistence: https://www.virusbulletin.com/uploads/pdf/conference/vb2014/VB2014-Wardle.pdf
- OSX Malware Detection: https://www.synack.com/wp-content/uploads/2016/03/RSA_OSX_Malware.pdf
- WireLurker: https://www.paloaltonetworks.com/content/dam/pan/en_US/assets/pdf/reports/Unit_42/unit42-wirelurker.pdf
