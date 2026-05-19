---
alias: T1136.001
---

## T1136.001

Adversaries may create a local account to maintain access to victim systems. Local accounts are those configured by an organization for use by users, remote support, services, or for administration on a single system or service. 

For example, with a sufficient level of access, the Windows <code>net user /add</code> command can be used to create a local account. On macOS systems the <code>dscl -create</code> command can be used to create a local account. Local accounts may also be added to network devices, often via common [Network Device CLI](https://attack.mitre.org/techniques/T1059/008) commands such as <code>username</code>, or to Kubernetes clusters using the `kubectl` utility.(Citation: cisco_username_cmd)(Citation: Kubernetes Service Accounts Security)

Such accounts may be used to establish secondary credentialed access that do not require persistent remote access tools to be deployed on the system.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Linux
- macOS
- Windows
- Network
- Containers

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Limit the number of accounts permitted to create other accounts. Limit the usage of local administrator accounts to be used for day-to-day operations that may expose them to potential adversaries. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Use multi-factor authentication for user and privileged accounts. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1136/001
- cisco_username_cmd: https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/security/s1/sec-s1-cr-book/sec-cr-t2.html#wp1047035630
- Kubernetes Service Accounts Security: https://kubernetes.io/docs/concepts/security/service-accounts/
- Microsoft User Creation Event: https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/event-4720
