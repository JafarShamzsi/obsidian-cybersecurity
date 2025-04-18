---
alias: T1027.001
---

## T1027.001

Adversaries may use binary padding to add junk data and change the on-disk representation of malware. This can be done without affecting the functionality or behavior of a binary, but can increase the size of the binary beyond what some security tools are capable of handling due to file size limitations. 

Binary padding effectively changes the checksum of the file and can also be used to avoid hash-based blocklists and static anti-virus signatures.(Citation: ESET OceanLotus) The padding used is commonly generated by a function to create junk data and then appended to the end or applied to sections of malware.(Citation: Securelist Malware Tricks April 2017) Increasing the file size may decrease the effectiveness of certain tools and detection capabilities that are not designed or configured to scan large files. This may also reduce the likelihood of being collected for analysis. Public file scanning services, such as VirusTotal, limits the maximum size of an uploaded file to be analyzed.(Citation: VirusTotal FAQ) 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1027/001
- ESET OceanLotus: https://www.welivesecurity.com/2018/03/13/oceanlotus-ships-new-backdoor/
- Securelist Malware Tricks April 2017: https://securelist.com/old-malware-tricks-to-bypass-detection-in-the-age-of-big-data/78010/
- VirusTotal FAQ: https://www.virustotal.com/en/faq/
