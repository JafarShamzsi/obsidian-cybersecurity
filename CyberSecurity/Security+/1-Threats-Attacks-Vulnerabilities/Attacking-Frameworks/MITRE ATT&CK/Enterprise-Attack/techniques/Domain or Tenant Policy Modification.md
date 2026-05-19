---
alias: T1484
---

## T1484

Adversaries may modify the configuration settings of a domain or identity tenant to evade defenses and/or escalate privileges in centrally managed environments. Such services provide a centralized means of managing identity resources such as devices and accounts, and often include configuration settings that may apply between domains or tenants such as trust relationships, identity syncing, or identity federation.

Modifications to domain or tenant settings may include altering domain Group Policy Objects (GPOs) in Microsoft Active Directory (AD) or changing trust settings for domains, including federation trusts relationships between domains or tenants.

With sufficient permissions, adversaries can modify domain or tenant policy settings. Since configuration settings for these services apply to a large number of identity resources, there are a great number of potential attacks malicious outcomes that can stem from this abuse. Examples of such abuse include:  

* modifying GPOs to push a malicious [Scheduled Task](https://attack.mitre.org/techniques/T1053/005) to computers throughout the domain environment(Citation: ADSecurity GPO Persistence 2016)(Citation: Wald0 Guide to GPOs)(Citation: Harmj0y Abusing GPO Permissions)
* modifying domain trusts to include an adversary-controlled domain, allowing adversaries to  forge access tokens that will subsequently be accepted by victim domain resources(Citation: Microsoft - Customer Guidance on Recent Nation-State Cyber Attacks)
* changing configuration settings within the AD environment to implement a [Rogue Domain Controller](https://attack.mitre.org/techniques/T1207).
* adding new, adversary-controlled federated identity providers to identity tenants, allowing adversaries to authenticate as any user managed by the victim tenant (Citation: Okta Cross-Tenant Impersonation 2023)

Adversaries may temporarily modify domain or tenant policy, carry out a malicious action(s), and then revert the change to remove suspicious indicators.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Windows
- Azure AD
- SaaS

### Permissions Required
- Administrator
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Consider implementing WMI and security filtering to further tailor which users and computers a GPO will apply to.(Citation: Wald0 Guide to GPOs)(Citation: Microsoft WMI Filters)(Citation: Microsoft GPO Security Filtering) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Use least privilege and protect administrative access to the Domain Controller and Active Directory Federation Services (AD FS) server. Do not create service accounts with administrative privileges. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Identify and correct GPO permissions abuse opportunities (ex: GPO modification privileges) using auditing tools such as [BloodHound](https://attack.mitre.org/software/S0521) (version 1.5.1 and later)(Citation: GitHub Bloodhound). |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Trust Modification\|T1484.002]] | Trust Modification |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Group Policy Modification\|T1484.001]] | Group Policy Modification |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1484
- CISA SolarWinds Cloud Detection: https://us-cert.cisa.gov/ncas/alerts/aa21-008a
- ADSecurity GPO Persistence 2016: https://adsecurity.org/?p=2716
- Microsoft 365 Defender Solorigate: https://www.microsoft.com/security/blog/2020/12/28/using-microsoft-365-defender-to-coordinate-protection-against-solorigate/
- Microsoft - Azure Sentinel ADFSDomainTrustMods: https://github.com/Azure/Azure-Sentinel/blob/master/Detections/AuditLogs/ADFSDomainTrustMods.yaml
- Microsoft - Update or Repair Federated domain: https://docs.microsoft.com/en-us/office365/troubleshoot/active-directory/update-federated-domain-office-365
- Microsoft - Customer Guidance on Recent Nation-State Cyber Attacks: https://msrc-blog.microsoft.com/2020/12/13/customer-guidance-on-recent-nation-state-cyber-attacks/
- Okta Cross-Tenant Impersonation 2023: https://sec.okta.com/articles/2023/08/cross-tenant-impersonation-prevention-and-detection
- Wald0 Guide to GPOs: https://wald0.com/?p=179
- Harmj0y Abusing GPO Permissions: http://www.harmj0y.net/blog/redteaming/abusing-gpo-permissions/
- Sygnia Golden SAML: https://www.sygnia.co/golden-saml-advisory
