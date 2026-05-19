---
alias: T1484.002
---

## T1484.002

Adversaries may add new domain trusts, modify the properties of existing domain trusts, or otherwise change the configuration of trust relationships between domains and tenants to evade defenses and/or elevate privileges.Trust details, such as whether or not user identities are federated, allow authentication and authorization properties to apply between domains or tenants for the purpose of accessing shared resources.(Citation: Microsoft - Azure AD Federation) These trust objects may include accounts, credentials, and other authentication material applied to servers, tokens, and domains.

Manipulating these trusts may allow an adversary to escalate privileges and/or evade defenses by modifying settings to add objects which they control. For example, in Microsoft Active Directory (AD) environments, this may be used to forge [SAML Tokens](https://attack.mitre.org/techniques/T1606/002) without the need to compromise the signing certificate to forge new credentials. Instead, an adversary can manipulate domain trusts to add their own signing certificate. An adversary may also convert an AD domain to a federated domain using Active Directory Federation Services (AD FS), which may enable malicious trust modifications such as altering the claim issuance rules to log in any valid set of credentials as a specified user.(Citation: AADInternals zure AD Federated Domain) 

An adversary may also add a new federated identity provider to an identity tenant such as Okta, which may enable the adversary to authenticate as any user of the tenant.(Citation: Okta Cross-Tenant Impersonation 2023)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Windows
- Azure AD
- SaaS

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Use the principal of least privilege and protect administrative access to domain trusts and identity tenants. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1484/002
- CISA SolarWinds Cloud Detection: https://us-cert.cisa.gov/ncas/alerts/aa21-008a
- AADInternals zure AD Federated Domain: https://o365blog.com/post/federation-vulnerability/
- Microsoft - Azure AD Federation: https://docs.microsoft.com/en-us/azure/active-directory/hybrid/whatis-fed
- Microsoft - Azure Sentinel ADFSDomainTrustMods: https://github.com/Azure/Azure-Sentinel/blob/master/Detections/AuditLogs/ADFSDomainTrustMods.yaml
- Microsoft - Update or Repair Federated domain: https://docs.microsoft.com/en-us/office365/troubleshoot/active-directory/update-federated-domain-office-365
- Okta Cross-Tenant Impersonation 2023: https://sec.okta.com/articles/2023/08/cross-tenant-impersonation-prevention-and-detection
- Sygnia Golden SAML: https://www.sygnia.co/golden-saml-advisory
