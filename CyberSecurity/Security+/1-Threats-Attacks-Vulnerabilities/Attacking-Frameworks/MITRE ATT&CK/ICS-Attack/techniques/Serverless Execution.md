---
alias: T1648
---

## T1648

Adversaries may abuse serverless computing, integration, and automation services to execute arbitrary code in cloud environments. Many cloud providers offer a variety of serverless resources, including compute engines, application integration services, and web servers. 

Adversaries may abuse these resources in various ways as a means of executing arbitrary commands. For example, adversaries may use serverless functions to execute malicious code, such as crypto-mining malware (i.e. [Resource Hijacking](https://attack.mitre.org/techniques/T1496)).(Citation: Cado Security Denonia) Adversaries may also create functions that enable further compromise of the cloud environment. For example, an adversary may use the `IAM:PassRole` permission in AWS or the `iam.serviceAccounts.actAs` permission in Google Cloud to add [Additional Cloud Roles](https://attack.mitre.org/techniques/T1098/003) to a serverless cloud function, which may then be able to perform actions the original user cannot.(Citation: Rhino Security Labs AWS Privilege Escalation)(Citation: Rhingo Security Labs GCP Privilege Escalation)

Serverless functions can also be invoked in response to cloud events (i.e. [Event Triggered Execution](https://attack.mitre.org/techniques/T1546)), potentially enabling persistent execution over time. For example, in AWS environments, an adversary may create a Lambda function that automatically adds [Additional Cloud Credentials](https://attack.mitre.org/techniques/T1098/001) to a user and a corresponding CloudWatch events rule that invokes that function whenever a new user is created.(Citation: Backdooring an AWS account) Similarly, an adversary may create a Power Automate workflow in Office 365 environments that forwards all emails a user receives or creates anonymous sharing links whenever a user is granted access to a document in SharePoint.(Citation: Varonis Power Automate Data Exfiltration)(Citation: Microsoft DART Case Report 001)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)

### Platforms
- SaaS
- IaaS
- Office 365

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Remove permissions to create, modify, or run serverless resources from users that do not explicitly require them. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1648
- Microsoft DART Case Report 001: https://www.microsoft.com/security/blog/2020/03/09/real-life-cybercrime-stories-dart-microsoft-detection-and-response-team
- Backdooring an AWS account: https://medium.com/daniel-grzelak/backdooring-an-aws-account-da007d36f8f9
- Varonis Power Automate Data Exfiltration: https://www.varonis.com/blog/power-automate-data-exfiltration
- Cado Security Denonia: https://www.cadosecurity.com/cado-discovers-denonia-the-first-malware-specifically-targeting-lambda/
- Rhino Security Labs AWS Privilege Escalation: https://rhinosecuritylabs.com/aws/aws-privilege-escalation-methods-mitigation/
- Rhingo Security Labs GCP Privilege Escalation: https://rhinosecuritylabs.com/gcp/privilege-escalation-google-cloud-platform-part-1/
