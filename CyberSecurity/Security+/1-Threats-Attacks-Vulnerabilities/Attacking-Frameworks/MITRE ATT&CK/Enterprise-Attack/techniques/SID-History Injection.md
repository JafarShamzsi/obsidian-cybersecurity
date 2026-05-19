---
alias: T1134.005
---

## T1134.005

Adversaries may use SID-History Injection to escalate privileges and bypass access controls. The Windows security identifier (SID) is a unique value that identifies a user or group account. SIDs are used by Windows security in both security descriptors and access tokens. (Citation: Microsoft SID) An account can hold additional SIDs in the SID-History Active Directory attribute (Citation: Microsoft SID-History Attribute), allowing inter-operable account migration between domains (e.g., all values in SID-History are included in access tokens).

With Domain Administrator (or equivalent) rights, harvested or well-known SID values (Citation: Microsoft Well Known SIDs Jun 2017) may be inserted into SID-History to enable impersonation of arbitrary users/groups such as Enterprise Administrators. This manipulation may result in elevated access to local resources and/or access to otherwise inaccessible domains via lateral movement techniques such as [Remote Services](https://attack.mitre.org/techniques/T1021), [SMB/Windows Admin Shares](https://attack.mitre.org/techniques/T1021/002), or [Windows Remote Management](https://attack.mitre.org/techniques/T1021/006).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Windows

### Permissions Required
- Administrator
- SYSTEM

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Active Directory Configuration\|M1015]] | Active Directory Configuration | Clean up SID-History attributes after legitimate account migration is complete.<br /><br />Consider applying SID Filtering to interforest trusts, such as forest trusts and external trusts, to exclude SID-History from requests to access domain resources. SID Filtering ensures that any authentication requests over a trust only contain SIDs of security principals from the trusted domain (i.e preventing the trusted domain from claiming a user has membership in groups outside of the domain).<br /><br />SID Filtering of forest trusts is enabled by default, but may have been disabled in some cases to allow a child domain to transitively access forest trusts. SID Filtering of external trusts is automatically enabled on all created external trusts using Server 2003 or later domain controllers. (Citation: Microsoft Trust Considerations Nov 2014) (Citation: Microsoft SID Filtering Quarantining Jan 2009) However note that SID Filtering is not automatically applied to legacy trusts or may have been deliberately disabled to allow inter-domain access to resources.<br /><br />SID Filtering can be applied by: (Citation: Microsoft Netdom Trust Sept 2012)<br /><br />* Disabling SIDHistory on forest trusts using the netdom tool (<code>netdom trust /domain: /EnableSIDHistory:no</code> on the domain controller)<br /><br />* Applying SID Filter Quarantining to external trusts using the netdom tool (<code>netdom trust <TrustingDomainName> /domain:<TrustedDomainName> /quarantine:yes</code> on the domain controller)<br /><br />* Applying SID Filtering to domain trusts within a single forest is not recommended as it is an unsupported configuration and can cause breaking changes. (Citation: Microsoft Netdom Trust Sept 2012) (Citation: AdSecurity Kerberos GT Aug 2015) If a domain within a forest is untrustworthy then it should not be a member of the forest. In this situation it is necessary to first split the trusted and untrusted domains into separate forests where SID Filtering can be applied to an interforest trust |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1134/005
- Microsoft SID: https://msdn.microsoft.com/library/windows/desktop/aa379571.aspx
- Microsoft SID-History Attribute: https://msdn.microsoft.com/library/ms679833.aspx
- Microsoft Well Known SIDs Jun 2017: https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems
- Microsoft Get-ADUser: https://technet.microsoft.com/library/ee617241.aspx
- AdSecurity SID History Sept 2015: https://adsecurity.org/?p=1772
- Microsoft DsAddSidHistory: https://msdn.microsoft.com/library/ms677982.aspx
