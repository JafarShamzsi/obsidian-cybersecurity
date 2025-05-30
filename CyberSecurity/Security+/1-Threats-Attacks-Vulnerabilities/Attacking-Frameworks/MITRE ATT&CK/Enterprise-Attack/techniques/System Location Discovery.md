---
alias: T1614
---

## T1614


Adversaries may gather information in an attempt to calculate the geographical location of a victim host. Adversaries may use the information from [System Location Discovery](https://attack.mitre.org/techniques/T1614) during automated discovery to shape follow-on behaviors, including whether or not the adversary fully infects the target and/or attempts specific actions.

Adversaries may attempt to infer the location of a system using various system checks, such as time zone, keyboard layout, and/or language settings.(Citation: FBI Ragnar Locker 2020)(Citation: Sophos Geolocation 2016)(Citation: Bleepingcomputer RAT malware 2020) Windows API functions such as <code>GetLocaleInfoW</code> can also be used to determine the locale of the host.(Citation: FBI Ragnar Locker 2020) In cloud environments, an instance's availability zone may also be discovered by accessing the instance metadata service from the instance.(Citation: AWS Instance Identity Documents)(Citation: Microsoft Azure Instance Metadata 2021)

Adversaries may also attempt to infer the location of a victim host using IP addressing, such as via online geolocation IP-lookup services.(Citation: Securelist Trasparent Tribe 2020)(Citation: Sophos Geolocation 2016)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows
- Linux
- macOS
- IaaS

### Permissions Required
- User

### Mitigations

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/System Language Discovery\|T1614.001]] | System Language Discovery |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1614
- FBI Ragnar Locker 2020: https://assets.documentcloud.org/documents/20413525/fbi-flash-indicators-of-compromise-ragnar-locker-ransomware-11192020-bc.pdf
- Sophos Geolocation 2016: https://news.sophos.com/en-us/2016/05/03/location-based-ransomware-threat-research/
- Bleepingcomputer RAT malware 2020: https://www.bleepingcomputer.com/news/security/new-rat-malware-gets-commands-via-discord-has-ransomware-feature/
- AWS Instance Identity Documents: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-identity-documents.html
- Microsoft Azure Instance Metadata 2021: https://docs.microsoft.com/en-us/azure/virtual-machines/windows/instance-metadata-service?tabs=windows
- Securelist Trasparent Tribe 2020: https://securelist.com/transparent-tribe-part-1/98127/
