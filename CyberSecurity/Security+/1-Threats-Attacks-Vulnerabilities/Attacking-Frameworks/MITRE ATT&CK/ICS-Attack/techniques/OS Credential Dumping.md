---
alias: T1003
---

## T1003

Adversaries may attempt to dump credentials to obtain account login and credential material, normally in the form of a hash or a clear text password. Credentials can be obtained from OS caches, memory, or structures.(Citation: Brining MimiKatz to Unix) Credentials can then be used to perform [Lateral Movement](https://attack.mitre.org/tactics/TA0008) and access restricted information.

Several of the tools mentioned in associated sub-techniques may be used by both adversaries and professional security testers. Additional custom tools likely exist as well.



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows
- Linux
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Training\|M1017]] | User Training | Limit credential overlap across accounts and systems by training users and administrators not to use the same password for multiple accounts. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Operating System Configuration\|M1028]] | Operating System Configuration | <br />Consider disabling or restricting NTLM.(Citation: Microsoft Disable NTLM Nov 2012) Consider disabling WDigest authentication.(Citation: Microsoft WDigest Mit) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Credential Access Protection\|M1043]] | Credential Access Protection | With Windows 10, Microsoft implemented new protections called Credential Guard to protect the LSA secrets that can be used to obtain credentials through forms of credential dumping. It is not configured by default and has hardware and firmware system requirements. (Citation: TechNet Credential Guard) It also does not protect against all forms of credential dumping. (Citation: GitHub SHB Credential Guard) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Process Integrity\|M1025]] | Privileged Process Integrity | <br />On Windows 8.1 and Windows Server 2012 R2, enable Protected Process Light for LSA.(Citation: Microsoft LSA) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Ensure that local administrator accounts have complex, unique passwords across all systems on the network. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | On Windows 10, enable Attack Surface Reduction (ASR) rules to secure LSASS and prevent credential stealing. (Citation: win10_asr) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Windows:<br />Do not put user or admin domain accounts in the local administrator groups across systems unless they are tightly controlled, as this is often equivalent to having a local administrator account with the same password on all systems. Follow best practices for design and administration of an enterprise network to limit privileged account use across administrative tiers.(Citation: Microsoft Securing Privileged Access)<br /><br />Linux:<br />Scraping the passwords from memory requires root privileges. Follow best practices in restricting access to privileged accounts to avoid hostile programs from accessing such sensitive regions of memory. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Active Directory Configuration\|M1015]] | Active Directory Configuration | <br />Manage the access control list for “Replicating Directory Changes” and other permissions associated with domain controller replication. (Citation: AdSecurity DCSync Sept 2015) (Citation: Microsoft Replication ACL) Consider adding users to the "Protected Users" Active Directory security group. This can help limit the caching of users' plaintext credentials.(Citation: Microsoft Protected Users Security Group) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Ensure Domain Controller backups are properly secured. |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Security Account Manager\|T1003.002]] | Security Account Manager |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/LSA Secrets\|T1003.004]] | LSA Secrets |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Proc Filesystem\|T1003.007]] | Proc Filesystem |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/LSASS Memory\|T1003.001]] | LSASS Memory |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Cached Domain Credentials\|T1003.005]] | Cached Domain Credentials |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/／etc／passwd and ／etc／shadow\|T1003.008]] | ／etc／passwd and ／etc／shadow |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/NTDS\|T1003.003]] | NTDS |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/DCSync\|T1003.006]] | DCSync |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1003
- Medium Detecting Attempts to Steal Passwords from Memory: https://medium.com/threatpunter/detecting-attempts-to-steal-passwords-from-memory-558f16dce4ea
- AdSecurity DCSync Sept 2015: https://adsecurity.org/?p=1729
- Microsoft DRSR Dec 2017: https://msdn.microsoft.com/library/cc228086.aspx
- Microsoft NRPC Dec 2017: https://msdn.microsoft.com/library/cc237008.aspx
- Microsoft GetNCCChanges: https://msdn.microsoft.com/library/dd207691.aspx
- Microsoft SAMR: https://msdn.microsoft.com/library/cc245496.aspx
- Powersploit: https://github.com/mattifestation/PowerSploit
- Samba DRSUAPI: https://wiki.samba.org/index.php/DRSUAPI
- Harmj0y DCSync Sept 2015: http://www.harmj0y.net/blog/redteaming/mimikatz-and-dcsync-and-extrasids-oh-my/
- Brining MimiKatz to Unix: https://labs.portcullis.co.uk/download/eu-18-Wadhwa-Brown-Where-2-worlds-collide-Bringing-Mimikatz-et-al-to-UNIX.pdf
