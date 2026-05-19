---
alias: T1184
---

## T1184

Secure Shell (SSH) is a standard means of remote access on Linux and macOS systems. It allows a user to connect to another system via an encrypted tunnel, commonly authenticating through a password, certificate or the use of an asymmetric encryption key pair.

In order to move laterally from a compromised host, adversaries may take advantage of trust relationships established with other systems via public key authentication in active SSH sessions by hijacking an existing connection to another system. This may occur through compromising the SSH agent itself or by having access to the agent's socket. If an adversary is able to obtain root access, then hijacking SSH sessions is likely trivial. (Citation: Slideshare Abusing SSH) (Citation: SSHjack Blackhat) (Citation: Clockwork SSH Agent Hijacking) Compromising the SSH agent also provides access to intercept SSH credentials. (Citation: Welivesecurity Ebury SSH)

[SSH Hijacking](https://attack.mitre.org/techniques/T1184) differs from use of [Remote Services](https://attack.mitre.org/techniques/T1021) because it injects into an existing SSH session rather than creating a new session using [Valid Accounts](https://attack.mitre.org/techniques/T1078).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Lateral Movement]] (TA0008)

### Platforms
- Linux
- macOS

### Permissions Required
- User
- root

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Control\|M1052]] | User Account Control | Ensure that all private keys are stored securely in locations where only the legitimate owner has access to with strong passwords and are rotated frequently. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Ensure SSH key pairs have strong passwords and refrain from using key-store technologies such as ssh-agent unless they are properly protected. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Ensure proper file permissions are set and harden system to prevent root privilege escalation opportunities. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Ensure proper file permissions are set and harden system to prevent root privilege escalation opportunities. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Ensure proper file permissions are set and harden system to prevent root privilege escalation opportunities. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Do not allow remote access via SSH as root or other privileged accounts. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Ensure that agent forwarding is disabled on systems that do not explicitly require this feature to prevent misuse. (Citation: Symantec SSH and ssh-agent) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1184
- Slideshare Abusing SSH: https://www.slideshare.net/morisson/mistrusting-and-abusing-ssh-13526219
- SSHjack Blackhat: https://www.blackhat.com/presentations/bh-usa-05/bh-us-05-boileau.pdf
- Clockwork SSH Agent Hijacking: https://www.clockwork.com/news/2012/09/28/602/ssh_agent_hijacking
- Welivesecurity Ebury SSH: https://www.welivesecurity.com/2014/02/21/an-in-depth-analysis-of-linuxebury/
