---
alias: T1599.001
---

## T1599.001

Adversaries may bridge network boundaries by modifying a network device’s Network Address Translation (NAT) configuration. Malicious modifications to NAT may enable an adversary to bypass restrictions on traffic routing that otherwise separate trusted and untrusted networks.

Network devices such as routers and firewalls that connect multiple networks together may implement NAT during the process of passing packets between networks. When performing NAT, the network device will rewrite the source and/or destination addresses of the IP address header. Some network designs require NAT for the packets to cross the border device.  A typical example of this is environments where internal networks make use of non-Internet routable addresses.(Citation: RFC1918)

When an adversary gains control of a network boundary device, they can either leverage existing NAT configurations to send traffic between two separated networks, or they can implement NAT configurations of their own design.  In the case of network designs that require NAT to function, this enables the adversary to overcome inherent routing limitations that would normally prevent them from accessing protected systems behind the border device.  In the case of network designs that do not require NAT, address translation can be used by adversaries to obscure their activities, as changing the addresses of packets that traverse a network boundary device can make monitoring data transmissions more challenging for defenders.  

Adversaries may use [Patch System Image](https://attack.mitre.org/techniques/T1601/001) to change the operating system of a network device, implementing their own custom NAT mechanisms to further obscure their activities


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Network

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Filter Network Traffic\|M1037]] | Filter Network Traffic | Block Traffic	Upon identifying a compromised network device being used to bridge a network boundary, block the malicious packets using an unaffected network device in path, such as a firewall or a router that has not been compromised.  Continue to monitor for additional activity and to ensure that the blocks are indeed effective. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Credential Access Protection\|M1043]] | Credential Access Protection | Some embedded network devices are capable of storing passwords for local accounts in either plain-text or encrypted formats.  Ensure that, where available, local passwords are always encrypted, per vendor recommendations. (Citation: Cisco IOS Software Integrity Assurance - AAA) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Refer to NIST guidelines when creating password policies. (Citation: NIST 800-63-3) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Restrict administrator accounts to as few individuals as possible, following least privilege principles.  Prevent credential overlap across systems of administrator and privileged accounts, particularly between network and non-network platforms, such as servers or endpoints. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Use multi-factor authentication for user and privileged accounts. Most embedded network devices support TACACS+ and/or RADIUS.  Follow vendor prescribed best practices for hardening access control. (Citation: Cisco IOS Software Integrity Assurance - TACACS) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1599/001
- RFC1918: https://tools.ietf.org/html/rfc1918
