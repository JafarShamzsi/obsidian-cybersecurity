---
alias: T1222.002
---

## T1222.002

Adversaries may modify file or directory permissions/attributes to evade access control lists (ACLs) and access protected files.(Citation: Hybrid Analysis Icacls1 June 2018)(Citation: Hybrid Analysis Icacls2 May 2018) File and directory permissions are commonly managed by ACLs configured by the file or directory owner, or users with the appropriate permissions. File and directory ACL implementations vary by platform, but generally explicitly designate which users or groups can perform which actions (read, write, execute, etc.).

Most Linux and Linux-based platforms provide a standard set of permission groups (user, group, and other) and a standard set of permissions (read, write, and execute) that are applied to each group. While nuances of each platform’s permissions implementation may vary, most of the platforms provide two primary commands used to manipulate file and directory ACLs: <code>chown</code> (short for change owner), and <code>chmod</code> (short for change mode).

Adversarial may use these commands to make themselves the owner of files and directories or change the mode if current permissions allow it. They could subsequently lock others out of the file. Specific file and directory modifications may be a required step for many techniques, such as establishing Persistence via [Unix Shell Configuration Modification](https://attack.mitre.org/techniques/T1546/004) or tainting/hijacking other instrumental binary/configuration files via [Hijack Execution Flow](https://attack.mitre.org/techniques/T1574).(Citation: 20 macOS Common Tools and Techniques) 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- macOS
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Applying more restrictive permissions to files and directories could prevent adversaries from modifying the access control lists. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Ensure critical system files as well as those known to be abused by adversaries have restrictive permissions and are owned by an appropriately privileged account, especially if access is not required by users nor will inhibit system functionality. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1222/002
- Hybrid Analysis Icacls1 June 2018: https://www.hybrid-analysis.com/sample/ef0d2628823e8e0a0de3b08b8eacaf41cf284c086a948bdfd67f4e4373c14e4d?environmentId=100
- Hybrid Analysis Icacls2 May 2018: https://www.hybrid-analysis.com/sample/22dab012c3e20e3d9291bce14a2bfc448036d3b966c6e78167f4626f5f9e38d6?environmentId=110
- 20 macOS Common Tools and Techniques: https://labs.sentinelone.com/20-common-tools-techniques-used-by-macos-threat-actors-malware/
