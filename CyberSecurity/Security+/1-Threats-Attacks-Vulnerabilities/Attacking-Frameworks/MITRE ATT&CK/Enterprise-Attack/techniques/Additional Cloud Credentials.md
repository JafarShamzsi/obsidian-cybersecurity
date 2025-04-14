---
alias: T1098.001
---

## T1098.001

Adversaries may add adversary-controlled credentials to a cloud account to maintain persistent access to victim accounts and instances within the environment.

For example, adversaries may add credentials for Service Principals and Applications in addition to existing legitimate credentials in Azure AD.(Citation: Microsoft SolarWinds Customer Guidance)(Citation: Blue Cloud of Death)(Citation: Blue Cloud of Death Video) These credentials include both x509 keys and passwords.(Citation: Microsoft SolarWinds Customer Guidance) With sufficient permissions, there are a variety of ways to add credentials including the Azure Portal, Azure command line interface, and Azure or Az PowerShell modules.(Citation: Demystifying Azure AD Service Principals)

In infrastructure-as-a-service (IaaS) environments, after gaining access through [Cloud Accounts](https://attack.mitre.org/techniques/T1078/004), adversaries may generate or import their own SSH keys using either the <code>CreateKeyPair</code> or <code>ImportKeyPair</code> API in AWS or the <code>gcloud compute os-login ssh-keys add</code> command in GCP.(Citation: GCP SSH Key Add) This allows persistent access to instances within the cloud environment without further usage of the compromised cloud accounts.(Citation: Expel IO Evil in AWS)(Citation: Expel Behind the Scenes)

Adversaries may also use the <code>CreateAccessKey</code> API in AWS or the <code>gcloud iam service-accounts keys create</code> command in GCP to add access keys to an account. If the target account has different permissions from the requesting account, the adversary may also be able to escalate their privileges in the environment (i.e. [Cloud Accounts](https://attack.mitre.org/techniques/T1078/004)).(Citation: Rhino Security Labs AWS Privilege Escalation)(Citation: Sysdig ScarletEel 2.0) For example, in Azure AD environments, an adversary with the Application Administrator role can add a new set of credentials to their application's service principal. In doing so the adversary would be able to access the service principal’s roles and permissions, which may be different from those of the Application Administrator.(Citation: SpecterOps Azure Privilege Escalation) 

In AWS environments, adversaries with the appropriate permissions may also use the `sts:GetFederationToken` API call to create a temporary set of credentials to [Forge Web Credentials](https://attack.mitre.org/techniques/T1606) tied to the permissions of the original user account. These temporary credentials may remain valid for the duration of their lifetime even if the original account’s API credentials are deactivated.
(Citation: Crowdstrike AWS User Federation Persistence)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- IaaS
- Azure AD
- SaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Network Segmentation\|M1030]] | Network Segmentation | Configure access controls and firewalls to limit access to critical systems and domain controllers. Most cloud environments support separate virtual private cloud (VPC) instances that enable further segmentation of cloud systems. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Ensure that low-privileged user accounts do not have permission to add access keys to accounts. In AWS environments, prohibit users from calling the `sts:GetFederationToken` API unless explicitly required.(Citation: Crowdstrike AWS User Federation Persistence) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Do not allow domain administrator or root accounts to be used for day-to-day operations that may expose them to potential adversaries on unprivileged systems. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Use multi-factor authentication for user and privileged accounts. Consider enforcing multi-factor authentication for the <code>CreateKeyPair</code> and <code>ImportKeyPair</code> API calls through IAM policies.(Citation: Expel IO Evil in AWS) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1098/001
- Crowdstrike AWS User Federation Persistence: https://www.crowdstrike.com/blog/how-adversaries-persist-with-aws-user-federation/
- Expel IO Evil in AWS: https://expel.io/blog/finding-evil-in-aws/
- SpecterOps Azure Privilege Escalation: https://posts.specterops.io/azure-privilege-escalation-via-service-principal-abuse-210ae2be2a5
- Demystifying Azure AD Service Principals: https://nedinthecloud.com/2019/07/16/demystifying-azure-ad-service-principals/
- GCP SSH Key Add: https://cloud.google.com/sdk/gcloud/reference/compute/os-login/ssh-keys/add
- Blue Cloud of Death Video: https://www.youtube.com/watch?v=wQ1CuAPnrLM&feature=youtu.be&t=2815
- Blue Cloud of Death: https://speakerdeck.com/tweekfawkes/blue-cloud-of-death-red-teaming-azure-1
- Microsoft SolarWinds Customer Guidance: https://msrc-blog.microsoft.com/2020/12/13/customer-guidance-on-recent-nation-state-cyber-attacks/
- Expel Behind the Scenes: https://expel.io/blog/behind-the-scenes-expel-soc-alert-aws/
- Sysdig ScarletEel 2.0: https://sysdig.com/blog/scarleteel-2-0/
- Rhino Security Labs AWS Privilege Escalation: https://rhinosecuritylabs.com/aws/aws-privilege-escalation-methods-mitigation/
