---
alias: T1601
---

## T1601

Adversaries may make changes to the operating system of embedded network devices to weaken defenses and provide new capabilities for themselves.  On such devices, the operating systems are typically monolithic and most of the device functionality and capabilities are contained within a single file.

To change the operating system, the adversary typically only needs to affect this one file, replacing or modifying it.  This can either be done live in memory during system runtime for immediate effect, or in storage to implement the change on the next boot of the network device.


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
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Refer to NIST guidelines when creating password policies. (Citation: NIST 800-63-3) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Restrict administrator accounts to as few individuals as possible, following least privilege principles.  Prevent credential overlap across systems of administrator and privileged accounts, particularly between network and non-network platforms, such as servers or endpoints. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Use multi-factor authentication for user and privileged accounts. Most embedded network devices support TACACS+ and/or RADIUS.  Follow vendor prescribed best practices for hardening access control.(Citation: Cisco IOS Software Integrity Assurance - TACACS) |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Patch System Image\|T1601.001]] | Patch System Image |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Downgrade System Image\|T1601.002]] | Downgrade System Image |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1601
- Cisco IOS Software Integrity Assurance - Image File Verification: https://tools.cisco.com/security/center/resources/integrity_assurance.html#7
- Cisco IOS Software Integrity Assurance - Run-Time Memory Verification: https://tools.cisco.com/security/center/resources/integrity_assurance.html#13
