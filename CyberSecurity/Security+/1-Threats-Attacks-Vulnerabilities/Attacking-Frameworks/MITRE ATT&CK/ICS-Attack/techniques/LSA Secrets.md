---
alias: T1003.004
---

## T1003.004

Adversaries with SYSTEM access to a host may attempt to access Local Security Authority (LSA) secrets, which can contain a variety of different credential materials, such as credentials for service accounts.(Citation: Passcape LSA Secrets)(Citation: Microsoft AD Admin Tier Model)(Citation: Tilbury Windows Credentials) LSA secrets are stored in the registry at <code>HKEY_LOCAL_MACHINE\SECURITY\Policy\Secrets</code>. LSA secrets can also be dumped from memory.(Citation: ired Dumping LSA Secrets)

[Reg](https://attack.mitre.org/software/S0075) can be used to extract from the Registry. [Mimikatz](https://attack.mitre.org/software/S0002) can be used to extract secrets from memory.(Citation: ired Dumping LSA Secrets)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows

### Permissions Required
- SYSTEM

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Training\|M1017]] | User Training | Limit credential overlap across accounts and systems by training users and administrators not to use the same password for multiple accounts. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Ensure that local administrator accounts have complex, unique passwords across all systems on the network. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Follow best practices for design and administration of an enterprise network to limit privileged account use across administrative tiers.(Citation: Tilbury Windows Credentials) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1003/004
- Passcape LSA Secrets: https://www.passcape.com/index.php?section=docsys&cmd=details&id=23
- Microsoft AD Admin Tier Model: https://docs.microsoft.com/en-us/windows-server/identity/securing-privileged-access/securing-privileged-access-reference-material?redirectedfrom=MSDN
- Tilbury Windows Credentials: https://www.first.org/resources/papers/conf2017/Windows-Credentials-Attacks-and-Mitigation-Techniques.pdf
- ired Dumping LSA Secrets: https://ired.team/offensive-security/credential-access-and-credential-dumping/dumping-lsa-secrets
- Powersploit: https://github.com/mattifestation/PowerSploit
