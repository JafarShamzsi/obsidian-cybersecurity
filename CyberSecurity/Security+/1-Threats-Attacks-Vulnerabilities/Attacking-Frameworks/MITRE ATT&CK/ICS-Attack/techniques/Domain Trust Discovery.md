---
alias: T1482
---

## T1482

Adversaries may attempt to gather information on domain trust relationships that may be used to identify lateral movement opportunities in Windows multi-domain/forest environments. Domain trusts provide a mechanism for a domain to allow access to resources based on the authentication procedures of another domain.(Citation: Microsoft Trusts) Domain trusts allow the users of the trusted domain to access resources in the trusting domain. The information discovered may help the adversary conduct [SID-History Injection](https://attack.mitre.org/techniques/T1134/005), [Pass the Ticket](https://attack.mitre.org/techniques/T1550/003), and [Kerberoasting](https://attack.mitre.org/techniques/T1558/003).(Citation: AdSecurity Forging Trust Tickets)(Citation: Harmj0y Domain Trusts) Domain trusts can be enumerated using the `DSEnumerateDomainTrusts()` Win32 API call, .NET methods, and LDAP.(Citation: Harmj0y Domain Trusts) The Windows utility [Nltest](https://attack.mitre.org/software/S0359) is known to be used by adversaries to enumerate domain trusts.(Citation: Microsoft Operation Wilysupply)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Network Segmentation\|M1030]] | Network Segmentation | Employ network segmentation for sensitive domains.(Citation: Harmj0y Domain Trusts). |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Map the trusts within existing domains/forests and keep trust relationships to a minimum. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1482
- Microsoft Operation Wilysupply: https://www.microsoft.com/security/blog/2017/05/04/windows-defender-atp-thwarts-operation-wilysupply-software-supply-chain-cyberattack/
- AdSecurity Forging Trust Tickets: https://adsecurity.org/?p=1588
- Microsoft Trusts: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc759554(v=ws.10)
- Microsoft GetAllTrustRelationships: https://docs.microsoft.com/en-us/dotnet/api/system.directoryservices.activedirectory.domain.getalltrustrelationships?redirectedfrom=MSDN&view=netframework-4.7.2#System_DirectoryServices_ActiveDirectory_Domain_GetAllTrustRelationships
- Harmj0y Domain Trusts: https://posts.specterops.io/a-guide-to-attacking-domain-trusts-971e52cb2944
