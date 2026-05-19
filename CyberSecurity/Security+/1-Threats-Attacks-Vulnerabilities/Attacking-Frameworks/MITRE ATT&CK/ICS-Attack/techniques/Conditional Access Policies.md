---
alias: T1556.009
---

## T1556.009

Adversaries may disable or modify conditional access policies to enable persistent access to compromised accounts. Conditional access policies are additional verifications used by identity providers and identity and access management systems to determine whether a user should be granted access to a resource.

For example, in Azure AD, Okta, and JumpCloud, users can be denied access to applications based on their IP address, device enrollment status, and use of multi-factor authentication.(Citation: Microsoft Conditional Access)(Citation: JumpCloud Conditional Access Policies)(Citation: Okta Conditional Access Policies) In some cases, identity providers may also support the use of risk-based metrics to deny sign-ins based on a variety of indicators. In AWS and GCP, IAM policies can contain `condition` attributes that verify arbitrary constraints such as the source IP, the date the request was made, and the nature of the resources or regions being requested.(Citation: AWS IAM Conditions)(Citation: GCP IAM Conditions) These measures help to prevent compromised credentials from resulting in unauthorized access to data or resources, as well as limit user permissions to only those required. 

By modifying conditional access policies, such as adding additional trusted IP ranges, removing [Multi-Factor Authentication](https://attack.mitre.org/techniques/T1556/006) requirements, or allowing additional [Unused/Unsupported Cloud Regions](https://attack.mitre.org/techniques/T1535), adversaries may be able to ensure persistent access to accounts and circumvent defensive measures.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Azure AD
- SaaS
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit permissions to modify conditional access policies to only those required. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1556/009
- AWS IAM Conditions: https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html
- GCP IAM Conditions: https://cloud.google.com/iam/docs/conditions-overview
- JumpCloud Conditional Access Policies: https://jumpcloud.com/support/get-started-conditional-access-policies
- Microsoft Conditional Access: https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview
- Okta Conditional Access Policies: https://support.okta.com/help/s/article/Conditional-access-based-on-device-security-posture?language=en_US
