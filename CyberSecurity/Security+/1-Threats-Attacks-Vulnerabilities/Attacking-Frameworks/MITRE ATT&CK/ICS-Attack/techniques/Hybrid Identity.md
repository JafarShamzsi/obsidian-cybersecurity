---
alias: T1556.007
---

## T1556.007

Adversaries may patch, modify, or otherwise backdoor cloud authentication processes that are tied to on-premises user identities in order to bypass typical authentication mechanisms, access credentials, and enable persistent access to accounts.  

Many organizations maintain hybrid user and device identities that are shared between on-premises and cloud-based environments. These can be maintained in a number of ways. For example, Azure AD includes three options for synchronizing identities between Active Directory and Azure AD(Citation: Azure AD Hybrid Identity):

* Password Hash Synchronization (PHS), in which a privileged on-premises account synchronizes user password hashes between Active Directory and Azure AD, allowing authentication to Azure AD to take place entirely in the cloud 
* Pass Through Authentication (PTA), in which Azure AD authentication attempts are forwarded to an on-premises PTA agent, which validates the credentials against Active Directory 
* Active Directory Federation Services (AD FS), in which a trust relationship is established between Active Directory and Azure AD 

AD FS can also be used with other SaaS and cloud platforms such as AWS and GCP, which will hand off the authentication process to AD FS and receive a token containing the hybrid users’ identity and privileges. 

By modifying authentication processes tied to hybrid identities, an adversary may be able to establish persistent privileged access to cloud resources. For example, adversaries who compromise an on-premises server running a PTA agent may inject a malicious DLL into the `AzureADConnectAuthenticationAgentService` process that authorizes all attempts to authenticate to Azure AD, as well as records user credentials.(Citation: Azure AD Connect for Read Teamers)(Citation: AADInternals Azure AD On-Prem to Cloud) In environments using AD FS, an adversary may edit the `Microsoft.IdentityServer.Servicehost` configuration file to load a malicious DLL that generates authentication tokens for any user with any set of claims, thereby bypassing multi-factor authentication and defined AD FS policies.(Citation: MagicWeb)

In some cases, adversaries may be able to modify the hybrid identity authentication process from the cloud. For example, adversaries who compromise a Global Administrator account in an Azure AD tenant may be able to register a new PTA agent via the web console, similarly allowing them to harvest credentials and log into the Azure AD environment as any user.(Citation: Mandiant Azure AD Backdoors)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows
- Azure AD
- SaaS
- Google Workspace
- Office 365
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Limit on-premises accounts with access to the hybrid identity solution in place. For example, limit Azure AD Global Administrator accounts to only those required, and ensure that these are dedicated cloud-only accounts rather than hybrid ones.(Citation: MagicWeb) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Integrating multi-factor authentication (MFA) as part of organizational policy can greatly reduce the risk of an adversary gaining control of valid credentials that may be used for additional tactics such as initial access, lateral movement, and collecting information. MFA can also be used to restrict access to cloud resources and APIs.  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Periodically review the hybrid identity solution in use for any discrepancies. For example, review all PTA agents in the Azure Management Portal to identify any unwanted or unapproved ones.(Citation: Mandiant Azure AD Backdoors) If ADFS is in use, review DLLs and executable files in the AD FS and Global Assembly Cache directories to ensure that they are signed by Microsoft. Note that in some cases binaries may be catalog-signed, which may cause the file to appear unsigned when viewing file properties.(Citation: MagicWeb) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1556/007
- Azure AD Connect for Read Teamers: https://blog.xpnsec.com/azuread-connect-for-redteam/
- AADInternals Azure AD On-Prem to Cloud: https://o365blog.com/post/on-prem_admin/
- MagicWeb: https://www.microsoft.com/security/blog/2022/08/24/magicweb-nobeliums-post-compromise-trick-to-authenticate-as-anyone/
- Azure AD Hybrid Identity: https://learn.microsoft.com/en-us/azure/active-directory/hybrid/choose-ad-authn
- Mandiant Azure AD Backdoors: https://www.mandiant.com/resources/detecting-microsoft-365-azure-active-directory-backdoors
