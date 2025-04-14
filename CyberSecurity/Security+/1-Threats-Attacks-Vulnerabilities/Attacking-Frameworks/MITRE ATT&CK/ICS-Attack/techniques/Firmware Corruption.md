---
alias: T1495
---

## T1495

Adversaries may overwrite or corrupt the flash memory contents of system BIOS or other firmware in devices attached to a system in order to render them inoperable or unable to boot, thus denying the availability to use the devices and/or the system.(Citation: Symantec Chernobyl W95.CIH) Firmware is software that is loaded and executed from non-volatile memory on hardware devices in order to initialize and manage device functionality. These devices may include the motherboard, hard drive, or video cards.

In general, adversaries may manipulate, overwrite, or corrupt firmware in order to deny the use of the system or devices. For example, corruption of firmware responsible for loading the operating system for network devices may render the network devices inoperable.(Citation: dhs_threat_to_net_devices)(Citation: cisa_malware_orgs_ukraine) Depending on the device, this attack may also result in [Data Destruction](https://attack.mitre.org/techniques/T1485). 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Impact]] (TA0040)

### Platforms
- Linux
- macOS
- Windows
- Network

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Boot Integrity\|M1046]] | Boot Integrity | Check the integrity of the existing BIOS and device firmware to determine if it is vulnerable to modification. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Prevent adversary access to privileged accounts or access necessary to replace system firmware. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Update Software\|M1051]] | Update Software | Patch the BIOS and other firmware as necessary to prevent successful use of known vulnerabilities. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1495
- cisa_malware_orgs_ukraine: https://www.cisa.gov/uscert/ncas/alerts/aa22-057a
- dhs_threat_to_net_devices: https://cyber.dhs.gov/assets/report/ar-16-20173.pdf
- MITRE Trustworthy Firmware Measurement: http://www.mitre.org/publications/project-stories/going-deep-into-the-bios-with-mitre-firmware-security-research
- Symantec Chernobyl W95.CIH: https://web.archive.org/web/20190508170055/https://www.symantec.com/security-center/writeup/2000-122010-2655-99
