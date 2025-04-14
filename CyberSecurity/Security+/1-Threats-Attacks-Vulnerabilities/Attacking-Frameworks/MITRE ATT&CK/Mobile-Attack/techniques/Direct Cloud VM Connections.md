---
alias: T1021.008
---

## T1021.008

Adversaries may leverage [Valid Accounts](https://attack.mitre.org/techniques/T1078) to log directly into accessible cloud hosted compute infrastructure through cloud native methods. Many cloud providers offer interactive connections to virtual infrastructure that can be accessed through the [Cloud API](https://attack.mitre.org/techniques/T1059/009), such as Azure Serial Console(Citation: Azure Serial Console), AWS EC2 Instance Connect(Citation: EC2 Instance Connect)(Citation: lucr-3: Getting SaaS-y in the cloud), and AWS System Manager.(Citation: AWS System Manager).

Methods of authentication for these connections can include passwords, application access tokens, or SSH keys. These cloud native methods may, by default, allow for privileged access on the host with SYSTEM or root level access. 

Adversaries may utilize these cloud native methods to directly access virtual infrastructure and pivot through an environment.(Citation: SIM Swapping and Abuse of the Microsoft Azure Serial Console) These connections typically provide direct console access to the VM rather than the execution of scripts (i.e., [Cloud Administration Command](https://attack.mitre.org/techniques/T1651)).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Lateral Movement]] (TA0008)

### Platforms
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit which users are allowed to access compute infrastructure via cloud native methods. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | If direct virtual machine connections are not required for administrative use, disable these connection types where feasible. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1021/008
- EC2 Instance Connect: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html
- AWS System Manager: https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html
- lucr-3: Getting SaaS-y in the cloud: https://permiso.io/blog/lucr-3-scattered-spider-getting-saas-y-in-the-cloud
- SIM Swapping and Abuse of the Microsoft Azure Serial Console: https://www.mandiant.com/resources/blog/sim-swapping-abuse-azure-serial
- Azure Serial Console: https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-machines/serial-console-overview
