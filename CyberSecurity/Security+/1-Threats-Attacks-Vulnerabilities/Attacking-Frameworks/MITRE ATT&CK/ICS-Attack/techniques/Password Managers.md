---
alias: T1555.005
---

## T1555.005

Adversaries may acquire user credentials from third-party password managers.(Citation: ise Password Manager February 2019) Password managers are applications designed to store user credentials, normally in an encrypted database. Credentials are typically accessible after a user provides a master password that unlocks the database. After the database is unlocked, these credentials may be copied to memory. These databases can be stored as files on disk.(Citation: ise Password Manager February 2019)

Adversaries may acquire user credentials from password managers by extracting the master password and/or plain-text credentials from memory.(Citation: FoxIT Wocao December 2019)(Citation: Github KeeThief) Adversaries may extract credentials from memory via [Exploitation for Credential Access](https://attack.mitre.org/techniques/T1212).(Citation: NVD CVE-2019-3610)
 Adversaries may also try brute forcing via [Password Guessing](https://attack.mitre.org/techniques/T1110/001) to obtain the master password of a password manager.(Citation: Cyberreason Anchor December 2019)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Refer to NIST guidelines when creating password policies for master passwords.(Citation: NIST 800-63-3) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Consider re-locking password managers after a short timeout to limit the time plaintext credentials live in memory from decrypted databases. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Update Software\|M1051]] | Update Software | Update password managers regularly by employing patch management for internal enterprise endpoints and servers. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1555/005
- ise Password Manager February 2019: https://www.ise.io/casestudies/password-manager-hacking/
- FoxIT Wocao December 2019: https://www.fox-it.com/media/kadlze5c/201912_report_operation_wocao.pdf
- Github KeeThief: https://github.com/GhostPack/KeeThief
- NVD CVE-2019-3610: https://nvd.nist.gov/vuln/detail/CVE-2019-3610
- Cyberreason Anchor December 2019: https://www.cybereason.com/blog/dropping-anchor-from-a-trickbot-infection-to-the-discovery-of-the-anchor-malware
