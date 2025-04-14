---
alias: T1019
---

## T1019

The BIOS (Basic Input/Output System) and The Unified Extensible Firmware Interface (UEFI) or Extensible Firmware Interface (EFI) are examples of system firmware that operate as the software interface between the operating system and hardware of a computer. (Citation: Wikipedia BIOS) (Citation: Wikipedia UEFI) (Citation: About UEFI)

System firmware like BIOS and (U)EFI underly the functionality of a computer and may be modified by an adversary to perform or assist in malicious activity. Capabilities exist to overwrite the system firmware, which may give sophisticated adversaries a means to install malicious firmware updates as a means of persistence on a system that may be difficult to detect.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows

### Permissions Required
- Administrator
- SYSTEM

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Boot Integrity\|M1046]] | Boot Integrity | Check the integrity of the existing BIOS or EFI to determine if it is vulnerable to modification. Use Trusted Platform Module technology. (Citation: TCG Trusted Platform Module) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Prevent adversary access to privileged accounts or access necessary to perform this technique. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Update Software\|M1051]] | Update Software | Patch the BIOS and EFI as necessary. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1019
- capec: https://capec.mitre.org/data/definitions/532.html
- Wikipedia BIOS: https://en.wikipedia.org/wiki/BIOS
- Wikipedia UEFI: https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface
- About UEFI: http://www.uefi.org/about
- MITRE Trustworthy Firmware Measurement: http://www.mitre.org/publications/project-stories/going-deep-into-the-bios-with-mitre-firmware-security-research
- MITRE Copernicus: http://www.mitre.org/capabilities/cybersecurity/overview/cybersecurity-blog/copernicus-question-your-assumptions-about
- McAfee CHIPSEC Blog: https://securingtomorrow.mcafee.com/business/chipsec-support-vault-7-disclosure-scanning/
- Github CHIPSEC: https://github.com/chipsec/chipsec
- Intel HackingTeam UEFI Rootkit: http://www.intelsecurity.com/advanced-threat-research/content/data/HT-UEFI-rootkit.html
