---
alias: T1136.003
---

## T1136.003

Adversaries may create a cloud account to maintain access to victim systems. With a sufficient level of access, such accounts may be used to establish secondary credentialed access that does not require persistent remote access tools to be deployed on the system.(Citation: Microsoft O365 Admin Roles)(Citation: Microsoft Support O365 Add Another Admin, October 2019)(Citation: AWS Create IAM User)(Citation: GCP Create Cloud Identity Users)(Citation: Microsoft Azure AD Users)

In addition to user accounts, cloud accounts may be associated with services. Cloud providers handle the concept of service accounts in different ways. In Azure, service accounts include service principals and managed identities, which can be linked to various resources such as OAuth applications, serverless functions, and virtual machines in order to grant those resources permissions to perform various activities in the environment.(Citation: Microsoft Entra ID Service Principals) In GCP, service accounts can also be linked to specific resources, as well as be impersonated by other accounts for [Temporary Elevated Cloud Access](https://attack.mitre.org/techniques/T1548/005).(Citation: GCP Service Accounts) While AWS has no specific concept of service accounts, resources can be directly granted permission to assume roles.(Citation: AWS Instance Profiles)(Citation: AWS Lambda Execution Role)

Adversaries may create accounts that only have access to specific cloud services, which can reduce the chance of detection.

Once an adversary has created a cloud account, they can then manipulate that account to ensure persistence and allow access to additional resources - for example, by adding [Additional Cloud Credentials](https://attack.mitre.org/techniques/T1098/001) or assigning [Additional Cloud Roles](https://attack.mitre.org/techniques/T1098/003).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Azure AD
- Office 365
- IaaS
- Google Workspace
- SaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Network Segmentation\|M1030]] | Network Segmentation | Configure access controls and firewalls to limit access to critical systems and domain controllers. Most cloud environments support separate virtual private cloud (VPC) instances that enable further segmentation of cloud systems. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Limit the number of accounts with permissions to create other accounts. Do not allow privileged accounts to be used for day-to-day operations that may expose them to potential adversaries on unprivileged systems. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Use multi-factor authentication for user and privileged accounts. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1136/003
- Microsoft O365 Admin Roles: https://docs.microsoft.com/en-us/office365/admin/add-users/about-admin-roles?view=o365-worldwide
- AWS Create IAM User: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html
- AWS Lambda Execution Role: https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html
- AWS Instance Profiles: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html
- GCP Create Cloud Identity Users: https://support.google.com/cloudidentity/answer/7332836?hl=en&ref_topic=7558554
- GCP Service Accounts: https://cloud.google.com/iam/docs/service-account-overview
- Microsoft Azure AD Users: https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/add-users-azure-active-directory
- Microsoft Entra ID Service Principals: https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals?tabs=browser
- Microsoft Support O365 Add Another Admin, October 2019: https://support.office.com/en-us/article/add-another-admin-f693489f-9f55-4bd0-a637-a81ce93de22d
