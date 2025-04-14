---
alias: T1483
---

## T1483

Adversaries may make use of Domain Generation Algorithms (DGAs) to dynamically identify a destination for command and control traffic rather than relying on a list of static IP addresses or domains. This has the advantage of making it much harder for defenders block, track, or take over the command and control channel, as there potentially could be thousands of domains that malware can check for instructions.(Citation: Cybereason Dissecting DGAs)(Citation: Cisco Umbrella DGA)(Citation: Unit 42 DGA Feb 2019)

DGAs can take the form of apparently random or “gibberish” strings (ex: istgmxdejdnxuyla.ru) when they construct domain names by generating each letter. Alternatively, some DGAs employ whole words as the unit by concatenating words together instead of letters (ex: cityjulydish.net). Many DGAs are time-based, generating a different domain for each time period (hourly, daily, monthly, etc). Others incorporate a seed value as well to make predicting future domains more difficult for defenders.(Citation: Cybereason Dissecting DGAs)(Citation: Cisco Umbrella DGA)(Citation: Talos CCleanup 2017)(Citation: Akamai DGA Mitigation)

Adversaries may use DGAs for the purpose of [Fallback Channels](https://attack.mitre.org/techniques/T1008). When contact is lost with the primary command and control server malware may employ a DGA as a means to reestablishing command and control.(Citation: Talos CCleanup 2017)(Citation: FireEye POSHSPY April 2017)(Citation: ESET Sednit 2017 Activity)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Command and Control]] (TA0011)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Network intrusion detection and prevention systems that use network signatures to identify traffic for specific adversary malware can be used to mitigate activity at the network level. Malware researchers can reverse engineer malware variants that use DGAs and determine future domains that the malware will attempt to contact, but this is a time and resource intensive effort.(Citation: Cybereason Dissecting DGAs)(Citation: Cisco Umbrella DGA Brute Force) Malware is also increasingly incorporating seed values that can be unique for each instance, which would then need to be determined to extract future generated domains. In some cases, the seed that a particular sample uses can be extracted from DNS traffic.(Citation: Akamai DGA Mitigation) Even so, there can be thousands of possible domains generated per day; this makes it impractical for defenders to preemptively register all possible C2 domains due to the cost. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict Web-Based Content\|M1021]] | Restrict Web-Based Content | In some cases a local DNS sinkhole may be used to help prevent DGA-based command and control at a reduced cost. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1483
- Cybereason Dissecting DGAs: http://go.cybereason.com/rs/996-YZT-709/images/Cybereason-Lab-Analysis-Dissecting-DGAs-Eight-Real-World-DGA-Variants.pdf
- Cisco Umbrella DGA: https://umbrella.cisco.com/blog/2016/10/10/domain-generation-algorithms-effective/
- Unit 42 DGA Feb 2019: https://unit42.paloaltonetworks.com/threat-brief-understanding-domain-generation-algorithms-dga/
- Talos CCleanup 2017: http://blog.talosintelligence.com/2017/09/avast-distributes-malware.html
- Akamai DGA Mitigation: https://blogs.akamai.com/2018/01/a-death-match-of-domain-generation-algorithms.html
- FireEye POSHSPY April 2017: https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html
- ESET Sednit 2017 Activity: https://www.welivesecurity.com/2017/12/21/sednit-update-fancy-bear-spent-year/
- Data Driven Security DGA: https://datadrivensecurity.info/blog/posts/2014/Oct/dga-part2/
- Pace University Detecting DGA May 2017: http://csis.pace.edu/~ctappert/srd2017/2017PDF/d4.pdf
- Elastic Predicting DGA: https://arxiv.org/pdf/1611.00791.pdf
