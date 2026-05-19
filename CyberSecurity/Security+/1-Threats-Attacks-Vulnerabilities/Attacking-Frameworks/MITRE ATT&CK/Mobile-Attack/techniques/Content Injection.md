---
alias: T1659
---

## T1659

Adversaries may gain access and continuously communicate with victims by injecting malicious content into systems through online network traffic. Rather than luring victims to malicious payloads hosted on a compromised website (i.e., [Drive-by Target](https://attack.mitre.org/techniques/T1608/004) followed by [Drive-by Compromise](https://attack.mitre.org/techniques/T1189)), adversaries may initially access victims through compromised data-transfer channels where they can manipulate traffic and/or inject their own content. These compromised online network channels may also be used to deliver additional payloads (i.e., [Ingress Tool Transfer](https://attack.mitre.org/techniques/T1105)) and other data to already compromised systems.(Citation: ESET MoustachedBouncer)

Adversaries may inject content to victim systems in various ways, including:

* From the middle, where the adversary is in-between legitimate online client-server communications (**Note:** this is similar but distinct from [Adversary-in-the-Middle](https://attack.mitre.org/techniques/T1557), which describes AiTM activity solely within an enterprise environment) (Citation: Kaspersky Encyclopedia MiTM)
* From the side, where malicious content is injected and races to the client as a fake response to requests of a legitimate online server (Citation: Kaspersky ManOnTheSide)

Content injection is often the result of compromised upstream communication channels, for example at the level of an internet service provider (ISP) as is the case with "lawful interception."(Citation: Kaspersky ManOnTheSide)(Citation: ESET MoustachedBouncer)(Citation: EFF China GitHub Attack)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Initial Access]] (TA0001)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Command and Control]] (TA0011)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict Web-Based Content\|M1021]] | Restrict Web-Based Content | Consider blocking download/transfer and execution of potentially uncommon file types known to be used in adversary campaigns. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Where possible, ensure that online traffic is appropriately encrypted through services such as trusted VPNs. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1659
- EFF China GitHub Attack: https://www.eff.org/deeplinks/2015/04/china-uses-unencrypted-websites-to-hijack-browsers-in-github-attack
- ESET MoustachedBouncer: https://www.welivesecurity.com/en/eset-research/moustachedbouncer-espionage-against-foreign-diplomats-in-belarus/
- Kaspersky Encyclopedia MiTM: https://encyclopedia.kaspersky.com/glossary/man-in-the-middle-attack/
- Kaspersky ManOnTheSide: https://usa.kaspersky.com/blog/man-on-the-side/27854/
