---
alias: T1200
---

## T1200

Adversaries may introduce computer accessories, networking hardware, or other computing devices into a system or network that can be used as a vector to gain access. Rather than just connecting and distributing payloads via removable storage (i.e. [Replication Through Removable Media](https://attack.mitre.org/techniques/T1091)), more robust hardware additions can be used to introduce new functionalities and/or features into a system that can then be abused.

While public references of usage by threat actors are scarce, many red teams/penetration testers leverage hardware additions for initial access. Commercial and open source products can be leveraged with capabilities such as passive network tapping, network traffic modification (i.e. [Adversary-in-the-Middle](https://attack.mitre.org/techniques/T1557)), keystroke injection, kernel memory reading via DMA, addition of new wireless access to an existing network, and others.(Citation: Ossmann Star Feb 2011)(Citation: Aleks Weapons Nov 2015)(Citation: Frisk DMA August 2016)(Citation: McMillan Pwn March 2012)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Initial Access]] (TA0001)

### Platforms
- Windows
- Linux
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Limit Access to Resource Over Network\|M1035]] | Limit Access to Resource Over Network | Establish network access control policies, such as using device certificates and the 802.1x standard. (Citation: Wikipedia 802.1x) Restrict use of DHCP to registered devices to prevent unregistered devices from communicating with trusted systems. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Limit Hardware Installation\|M1034]] | Limit Hardware Installation | Block unknown devices and accessories by endpoint security configuration and monitoring agent. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1200
- Ossmann Star Feb 2011: https://ossmann.blogspot.com/2011/02/throwing-star-lan-tap.html
- Aleks Weapons Nov 2015: https://www.youtube.com/watch?v=lDvf4ScWbcQ
- McMillan Pwn March 2012: https://arstechnica.com/information-technology/2012/03/the-pwn-plug-is-a-little-white-box-that-can-hack-your-network/
- Frisk DMA August 2016: https://www.youtube.com/watch?v=fXthwl6ShOg
