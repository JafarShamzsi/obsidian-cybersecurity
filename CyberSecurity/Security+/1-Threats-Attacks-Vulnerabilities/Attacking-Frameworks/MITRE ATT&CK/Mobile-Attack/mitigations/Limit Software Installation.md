---
alias: M1033
---

## M1033

Block users or groups from installing unapproved software.


### Techniques Addressed by Mitigation

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Browser Extensions\|T1176]] | Browser Extensions | Only install browser extensions from trusted sources that can be verified. Browser extensions for some browsers can be controlled through Group Policy. Change settings to prevent the browser from installing extensions without sufficient permissions. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Compromise Software Dependencies and Development Tools\|T1195.001]] | Compromise Software Dependencies and Development Tools | Where possible, consider requiring developers to pull from internal repositories containing verified and approved packages rather than from external ones.(Citation: Cider Security Top 10 CICD Security Risks) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Hide Artifacts\|T1564]] | Hide Artifacts | Restrict the installation of software that may be abused to create hidden desktops, such as hVNC, to user groups that require it. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Create or Modify System Process\|T1543]] | Create or Modify System Process | Restrict software installation to trusted repositories only and be cautious of orphaned software packages. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Hidden Window\|T1564.003]] | Hidden Window | Restrict the installation of software that may be abused to create hidden desktops, such as hVNC, to user groups that require it. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Software Deployment Tools\|T1072]] | Software Deployment Tools | Restrict the use of third-party software suites installed within an enterprise network.  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/XDG Autostart Entries\|T1547.013]] | XDG Autostart Entries | Restrict software installation to trusted repositories only and be cautious of orphaned software packages. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Python\|T1059.006]] | Python | Prevent users from installing Python where not required. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Supply Chain Compromise\|T1195]] | Supply Chain Compromise | Where possible, consider requiring developers to pull from internal repositories containing verified and approved packages rather than from external ones.(Citation: Cider Security Top 10 CICD Security Risks) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Systemd Service\|T1543.002]] | Systemd Service | Restrict software installation to trusted repositories only and be cautious of orphaned software packages. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/VNC\|T1021.005]] | VNC | Restrict software installation to user groups that require it. A VNC server must be manually installed by the user or adversary. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Systemd Service\|T1501]] | Systemd Service | Restrict software installation to trusted repositories only and be cautious of orphaned software packages. |
