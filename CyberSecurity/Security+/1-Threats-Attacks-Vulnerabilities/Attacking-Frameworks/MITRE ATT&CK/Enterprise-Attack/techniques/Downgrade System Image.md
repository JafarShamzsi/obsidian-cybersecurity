---
alias: T1601.002
---

## T1601.002

Adversaries may install an older version of the operating system of a network device to weaken security.  Older operating system versions on network devices often have weaker encryption ciphers and, in general, fewer/less updated defensive features. (Citation: Cisco Synful Knock Evolution)

On embedded devices, downgrading the version typically only requires replacing the operating system file in storage.  With most embedded devices, this can be achieved by downloading a copy of the desired version of the operating system file and reconfiguring the device to boot from that file on next system restart.  The adversary could then restart the device to implement the change immediately or they could wait until the next time the system restarts.

Downgrading the system image to an older versions may allow an adversary to evade defenses by enabling behaviors such as [Weaken Encryption](https://attack.mitre.org/techniques/T1600).  Downgrading of a system image can be done on its own, or it can be used in conjunction with [Patch System Image](https://attack.mitre.org/techniques/T1601/001).  


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Network

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Credential Access Protection\|M1043]] | Credential Access Protection | Some embedded network devices are capable of storing passwords for local accounts in either plain-text or encrypted formats.  Ensure that, where available, local passwords are always encrypted, per vendor recommendations. (Citation: Cisco IOS Software Integrity Assurance - Credentials Management) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Code Signing\|M1045]] | Code Signing | Many vendors provide digitally signed operating system images to validate the integrity of the software used on their platform.  Make use of this feature where possible in order to prevent and/or detect attempts by adversaries to compromise the system image. (Citation: Cisco IOS Software Integrity Assurance - Deploy Signed IOS) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Boot Integrity\|M1046]] | Boot Integrity | Some vendors of embedded network devices provide cryptographic signing to ensure the integrity of operating system images at boot time.  Implement where available, following vendor guidelines. (Citation: Cisco IOS Software Integrity Assurance - Secure Boot) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Refer to NIST guidelines when creating password policies.  (Citation: NIST 800-63-3) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Restrict administrator accounts to as few individuals as possible, following least privilege principles.  Prevent credential overlap across systems of administrator and privileged accounts, particularly between network and non-network platforms, such as servers or endpoints. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Use multi-factor authentication for user and privileged accounts. Most embedded network devices support TACACS+ and/or RADIUS.  Follow vendor prescribed best practices for hardening access control.(Citation: Cisco IOS Software Integrity Assurance - TACACS) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1601/002
- Cisco Synful Knock Evolution: https://blogs.cisco.com/security/evolution-of-attacks-on-cisco-ios-devices
