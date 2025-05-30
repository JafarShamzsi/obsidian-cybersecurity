---
alias: T1547.014
---

## T1547.014

Adversaries may achieve persistence by adding a Registry key to the Active Setup of the local machine. Active Setup is a Windows mechanism that is used to execute programs when a user logs in. The value stored in the Registry key will be executed after a user logs into the computer.(Citation: Klein Active Setup 2010) These programs will be executed under the context of the user and will have the account's associated permissions level.

Adversaries may abuse Active Setup by creating a key under <code> HKLM\SOFTWARE\Microsoft\Active Setup\Installed Components\</code> and setting a malicious value for <code>StubPath</code>. This value will serve as the program that will be executed when a user logs into the computer.(Citation: Mandiant Glyer APT 2010)(Citation: Citizenlab Packrat 2015)(Citation: FireEye CFR Watering Hole 2012)(Citation: SECURELIST Bright Star 2015)(Citation: paloalto Tropic Trooper 2016)

Adversaries can abuse these components to execute malware, such as remote access tools, to maintain persistence through system reboots. Adversaries may also use [Masquerading](https://attack.mitre.org/techniques/T1036) to make the Registry entries look as if they are associated with legitimate programs.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Windows

### Permissions Required
- Administrator

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1547/014
- SECURELIST Bright Star 2015: https://securelist.com/whos-really-spreading-through-the-bright-star/68978/
- Mandiant Glyer APT 2010: https://digital-forensics.sans.org/summit-archives/2010/35-glyer-apt-persistence-mechanisms.pdf
- FireEye CFR Watering Hole 2012: https://www.fireeye.com/blog/threat-research/2012/12/council-foreign-relations-water-hole-attack-details.html
- Klein Active Setup 2010: https://helgeklein.com/blog/2010/04/active-setup-explained/
- paloalto Tropic Trooper 2016: https://unit42.paloaltonetworks.com/unit42-tropic-trooper-targets-taiwanese-government-and-fossil-fuel-provider-with-poison-ivy/
- TechNet Autoruns: https://technet.microsoft.com/en-us/sysinternals/bb963902
- Citizenlab Packrat 2015: https://citizenlab.ca/2015/12/packrat-report/
