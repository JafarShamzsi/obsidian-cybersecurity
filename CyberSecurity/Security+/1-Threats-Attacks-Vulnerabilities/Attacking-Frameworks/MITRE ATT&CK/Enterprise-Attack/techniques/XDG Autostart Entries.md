---
alias: T1547.013
---

## T1547.013

Adversaries may add or modify XDG Autostart Entries to execute malicious programs or commands when a user’s desktop environment is loaded at login. XDG Autostart entries are available for any XDG-compliant Linux system. XDG Autostart entries use Desktop Entry files (`.desktop`) to configure the user’s desktop environment upon user login. These configuration files determine what applications launch upon user login, define associated applications to open specific file types, and define applications used to open removable media.(Citation: Free Desktop Application Autostart Feb 2006)(Citation: Free Desktop Entry Keys)

Adversaries may abuse this feature to establish persistence by adding a path to a malicious binary or command to the `Exec` directive in the `.desktop` configuration file. When the user’s desktop environment is loaded at user login, the `.desktop` files located in the XDG Autostart directories are automatically executed. System-wide Autostart entries are located in the `/etc/xdg/autostart` directory while the user entries are located in the `~/.config/autostart` directory.

Adversaries may combine this technique with [Masquerading](https://attack.mitre.org/techniques/T1036) to blend malicious Autostart entries with legitimate programs.(Citation: Red Canary Netwire Linux 2022)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Linux

### Permissions Required
- User
- root

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Limit Software Installation\|M1033]] | Limit Software Installation | Restrict software installation to trusted repositories only and be cautious of orphaned software packages. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit privileges of user accounts so only authorized privileged users can create and modify XDG autostart entries. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Restrict write access to XDG autostart entries to only select privileged users. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1547/013
- Free Desktop Application Autostart Feb 2006: https://specifications.freedesktop.org/autostart-spec/autostart-spec-latest.html
- Free Desktop Entry Keys: https://specifications.freedesktop.org/desktop-entry-spec/1.2/ar01s06.html
- Red Canary Netwire Linux 2022: https://redcanary.com/blog/netwire-remote-access-trojan-on-linux/
