---
alias: T1522
---

## T1522

Adversaries may attempt to access the Cloud Instance Metadata API to collect credentials and other sensitive data.

Most cloud service providers support a Cloud Instance Metadata API which is a service provided to running virtual instances that allows applications to access information about the running virtual instance. Available information generally includes name, security group, and additional metadata including sensitive data such as credentials and UserData scripts that may contain additional secrets. The Instance Metadata API is provided as a convenience to assist in managing applications and is accessible by anyone who can access the instance.(Citation: AWS Instance Metadata API)

If adversaries have a presence on the running virtual instance, they may query the Instance Metadata API directly to identify credentials that grant access to additional resources. Additionally, attackers may exploit a Server-Side Request Forgery (SSRF) vulnerability in a public facing web proxy that allows the attacker to gain access to the sensitive information via a request to the Instance Metadata API.(Citation: RedLock Instance Metadata API 2018)

The de facto standard across cloud service providers is to host the Instance Metadata API at <code>http[:]//169.254.169.254</code>.



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- IaaS

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Filter Network Traffic\|M1037]] | Filter Network Traffic | Limit access to the Instance Metadata API using a host-based firewall such as iptables.(Citation: RedLock Instance Metadata API 2018) A properly configured Web Application Firewall (WAF) may help prevent external adversaries from exploiting Server-side Request Forgery (SSRF) attacks that allow access to the Cloud Instance Metadata API. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1522
- AWS Instance Metadata API: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html
- RedLock Instance Metadata API 2018: https://redlock.io/blog/instance-metadata-api-a-modern-day-trojan-horse
