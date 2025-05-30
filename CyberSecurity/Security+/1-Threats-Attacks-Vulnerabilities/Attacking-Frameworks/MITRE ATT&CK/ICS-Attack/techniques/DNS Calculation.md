---
alias: T1568.003
---

## T1568.003

Adversaries may perform calculations on addresses returned in DNS results to determine which port and IP address to use for command and control, rather than relying on a predetermined port number or the actual returned IP address. A IP and/or port number calculation can be used to bypass egress filtering on a C2 channel.(Citation: Meyers Numbered Panda)

One implementation of [DNS Calculation](https://attack.mitre.org/techniques/T1568/003) is to take the first three octets of an IP address in a DNS response and use those values to calculate the port for command and control traffic.(Citation: Meyers Numbered Panda)(Citation: Moran 2014)(Citation: Rapid7G20Espionage)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Command and Control]] (TA0011)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1568/003
- Meyers Numbered Panda: http://www.crowdstrike.com/blog/whois-numbered-panda/
- Moran 2014: https://www.fireeye.com/blog/threat-research/2014/09/darwins-favorite-apt-group-2.html
- Rapid7G20Espionage: https://blog.rapid7.com/2013/08/26/upcoming-g20-summit-fuels-espionage-operations/
