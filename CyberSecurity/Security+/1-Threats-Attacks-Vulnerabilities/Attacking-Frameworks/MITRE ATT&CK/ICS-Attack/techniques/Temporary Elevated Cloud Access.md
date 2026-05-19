---
alias: T1548.005
---

## T1548.005

Adversaries may abuse permission configurations that allow them to gain temporarily elevated access to cloud resources. Many cloud environments allow administrators to grant user or service accounts permission to request just-in-time access to roles, impersonate other accounts, pass roles onto resources and services, or otherwise gain short-term access to a set of privileges that may be distinct from their own. 

Just-in-time access is a mechanism for granting additional roles to cloud accounts in a granular, temporary manner. This allows accounts to operate with only the permissions they need on a daily basis, and to request additional permissions as necessary. Sometimes just-in-time access requests are configured to require manual approval, while other times the desired permissions are automatically granted.(Citation: Azure Just in Time Access 2023)

Account impersonation allows user or service accounts to temporarily act with the permissions of another account. For example, in GCP users with the `iam.serviceAccountTokenCreator` role can create temporary access tokens or sign arbitrary payloads with the permissions of a service account, while service accounts with domain-wide delegation permission are permitted to impersonate Google Workspace accounts.(Citation: Google Cloud Service Account Authentication Roles)(Citation: Hunters Domain Wide Delegation Google Workspace 2023)(Citation: Google Cloud Just in Time Access 2023)(Citation: Palo Alto Unit 42 Google Workspace Domain Wide Delegation 2023) In Exchange Online, the `ApplicationImpersonation` role allows a service account to use the permissions associated with specified user accounts.(Citation: Microsoft Impersonation and EWS in Exchange) 

Many cloud environments also include mechanisms for users to pass roles to resources that allow them to perform tasks and authenticate to other services. While the user that creates the resource does not directly assume the role they pass to it, they may still be able to take advantage of the role's access -- for example, by configuring the resource to perform certain actions with the permissions it has been granted. In AWS, users with the `PassRole` permission can allow a service they create to assume a given role, while in GCP, users with the `iam.serviceAccountUser` role can attach a service account to a resource.(Citation: AWS PassRole)(Citation: Google Cloud Service Account Authentication Roles)

While users require specific role assignments in order to use any of these features, cloud administrators may misconfigure permissions. This could result in escalation paths that allow adversaries to gain access to resources beyond what was originally intended.(Citation: Rhino Google Cloud Privilege Escalation)(Citation: Rhino Security Labs AWS Privilege Escalation)

**Note:** this technique is distinct from [Additional Cloud Roles](https://attack.mitre.org/techniques/T1098/003), which involves assigning permanent roles to accounts rather than abusing existing permissions structures to gain temporarily elevated access to resources. However, adversaries that compromise a sufficiently privileged account may grant another account they control [Additional Cloud Roles](https://attack.mitre.org/techniques/T1098/003) that would allow them to also abuse these features. This may also allow for greater stealth than would be had by directly using the highly privileged account, especially when logs do not clarify when role impersonation is taking place.(Citation: CrowdStrike StellarParticle January 2022)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- IaaS
- Azure AD
- Office 365
- Google Workspace

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit the privileges of cloud accounts to assume, create, or impersonate additional roles, policies, and permissions to only those required. Where just-in-time access is enabled, consider requiring manual approval for temporary elevation of privileges. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1548/005
- AWS PassRole: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_passrole.html
- CrowdStrike StellarParticle January 2022: https://www.crowdstrike.com/blog/observations-from-the-stellarparticle-campaign/
- Google Cloud Just in Time Access 2023: https://cloud.google.com/architecture/manage-just-in-time-privileged-access-to-project
- Google Cloud Service Account Authentication Roles: https://cloud.google.com/iam/docs/service-account-permissions
- Microsoft Impersonation and EWS in Exchange: https://learn.microsoft.com/en-us/exchange/client-developer/exchange-web-services/impersonation-and-ews-in-exchange
- Azure Just in Time Access 2023: https://learn.microsoft.com/en-us/azure/azure-resource-manager/managed-applications/approve-just-in-time-access
- Rhino Security Labs AWS Privilege Escalation: https://rhinosecuritylabs.com/aws/aws-privilege-escalation-methods-mitigation/
- Rhino Google Cloud Privilege Escalation: https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/
- Hunters Domain Wide Delegation Google Workspace 2023: https://www.hunters.security/en/blog/delefriend-a-newly-discovered-design-flaw-in-domain-wide-delegation-could-leave-google-workspace-vulnerable-for-takeover
- Palo Alto Unit 42 Google Workspace Domain Wide Delegation 2023: https://unit42.paloaltonetworks.com/critical-risk-in-google-workspace-delegation-feature/
