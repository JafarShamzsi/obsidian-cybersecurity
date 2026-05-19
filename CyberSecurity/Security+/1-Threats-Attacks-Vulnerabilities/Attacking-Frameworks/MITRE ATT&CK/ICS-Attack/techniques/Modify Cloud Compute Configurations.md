---
alias: T1578.005
---

## T1578.005

Adversaries may modify settings that directly affect the size, locations, and resources available to cloud compute infrastructure in order to evade defenses. These settings may include service quotas, subscription associations, tenant-wide policies, or other configurations that impact available compute. Such modifications may allow adversaries to abuse the victim’s compute resources to achieve their goals, potentially without affecting the execution of running instances and/or revealing their activities to the victim.

For example, cloud providers often limit customer usage of compute resources via quotas. Customers may request adjustments to these quotas to support increased computing needs, though these adjustments may require approval from the cloud provider. Adversaries who compromise a cloud environment may similarly request quota adjustments in order to support their activities, such as enabling additional [Resource Hijacking](https://attack.mitre.org/techniques/T1496) without raising suspicion by using up a victim’s entire quota.(Citation: Microsoft Cryptojacking 2023) Adversaries may also increase allowed resource usage by modifying any tenant-wide policies that limit the sizes of deployed virtual machines.(Citation: Microsoft Azure Policy)

Adversaries may also modify settings that affect where cloud resources can be deployed, such as enabling [Unused/Unsupported Cloud Regions](https://attack.mitre.org/techniques/T1535). In Azure environments, an adversary who has gained access to a Global Administrator account may create new subscriptions in which to deploy resources, or engage in subscription hijacking by transferring an existing pay-as-you-go subscription from a victim tenant to an adversary-controlled tenant.(Citation: Microsoft Peach Sandstorm 2023) This will allow the adversary to use the victim’s compute resources without generating logs on the victim tenant.(Citation: Microsoft Azure Policy) (Citation: Microsoft Subscription Hijacking 2022)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit permissions to request quotas adjustments or modify tenant-level compute setting to only those required. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Routinely monitor user permissions to ensure only the expected users have the capability to request quota adjustments or modify tenant-level compute settings. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1578/005
- Microsoft Subscription Hijacking 2022: https://techcommunity.microsoft.com/t5/microsoft-365-defender-blog/hunt-for-compromised-azure-subscriptions-using-microsoft/ba-p/3607121
- Microsoft Cryptojacking 2023: https://www.microsoft.com/en-us/security/blog/2023/07/25/cryptojacking-understanding-and-defending-against-cloud-compute-resource-abuse/
- Microsoft Peach Sandstorm 2023: https://www.microsoft.com/en-us/security/blog/2023/09/14/peach-sandstorm-password-spray-campaigns-enable-intelligence-collection-at-high-value-targets/
- Microsoft Azure Policy: https://learn.microsoft.com/en-us/azure/governance/policy/samples/built-in-policies#compute
