---
alias: T1003.006
---

## T1003.006

Adversaries may attempt to access credentials and other sensitive information by abusing a Windows Domain Controller's application programming interface (API)(Citation: Microsoft DRSR Dec 2017) (Citation: Microsoft GetNCCChanges) (Citation: Samba DRSUAPI) (Citation: Wine API samlib.dll) to simulate the replication process from a remote domain controller using a technique called DCSync.

Members of the Administrators, Domain Admins, and Enterprise Admin groups or computer accounts on the domain controller are able to run DCSync to pull password data(Citation: ADSecurity Mimikatz DCSync) from Active Directory, which may include current and historical hashes of potentially useful accounts such as KRBTGT and Administrators. The hashes can then in turn be used to create a [Golden Ticket](https://attack.mitre.org/techniques/T1558/001) for use in [Pass the Ticket](https://attack.mitre.org/techniques/T1550/003)(Citation: Harmj0y Mimikatz and DCSync) or change an account's password as noted in [Account Manipulation](https://attack.mitre.org/techniques/T1098).(Citation: InsiderThreat ChangeNTLM July 2017)

DCSync functionality has been included in the "lsadump" module in [Mimikatz](https://attack.mitre.org/software/S0002).(Citation: GitHub Mimikatz lsadump Module) Lsadump also includes NetSync, which performs DCSync over a legacy replication protocol.(Citation: Microsoft NRPC Dec 2017)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Ensure that local administrator accounts have complex, unique passwords across all systems on the network. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Do not put user or admin domain accounts in the local administrator groups across systems unless they are tightly controlled, as this is often equivalent to having a local administrator account with the same password on all systems. Follow best practices for design and administration of an enterprise network to limit privileged account use across administrative tiers. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Active Directory Configuration\|M1015]] | Active Directory Configuration | Manage the access control list for "Replicating Directory Changes" and other permissions associated with domain controller replication.(Citation: ADSecurity Mimikatz DCSync)(Citation: Microsoft Replication ACL) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1003/006
- Microsoft DRSR Dec 2017: https://msdn.microsoft.com/library/cc228086.aspx
- Microsoft GetNCCChanges: https://msdn.microsoft.com/library/dd207691.aspx
- Samba DRSUAPI: https://wiki.samba.org/index.php/DRSUAPI
- Wine API samlib.dll: https://source.winehq.org/WineAPI/samlib.html
- ADSecurity Mimikatz DCSync: https://adsecurity.org/?p=1729
- Harmj0y Mimikatz and DCSync: http://www.harmj0y.net/blog/redteaming/mimikatz-and-dcsync-and-extrasids-oh-my/
- InsiderThreat ChangeNTLM July 2017: https://blog.stealthbits.com/manipulating-user-passwords-with-mimikatz-SetNTLM-ChangeNTLM
- GitHub Mimikatz lsadump Module: https://github.com/gentilkiwi/mimikatz/wiki/module-~-lsadump
- Microsoft NRPC Dec 2017: https://msdn.microsoft.com/library/cc237008.aspx
- Microsoft SAMR: https://msdn.microsoft.com/library/cc245496.aspx
- AdSecurity DCSync Sept 2015: https://adsecurity.org/?p=1729
- Harmj0y DCSync Sept 2015: http://www.harmj0y.net/blog/redteaming/mimikatz-and-dcsync-and-extrasids-oh-my/
