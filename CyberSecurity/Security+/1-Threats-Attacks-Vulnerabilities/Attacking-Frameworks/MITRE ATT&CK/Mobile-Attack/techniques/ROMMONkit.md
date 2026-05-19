---
alias: T1542.004
---

## T1542.004

Adversaries may abuse the ROM Monitor (ROMMON) by loading an unauthorized firmware with adversary code to provide persistent access and manipulate device behavior that is difficult to detect. (Citation: Cisco Synful Knock Evolution)(Citation: Cisco Blog Legacy Device Attacks)


ROMMON is a Cisco network device firmware that functions as a boot loader, boot image, or boot helper to initialize hardware and software when the platform is powered on or reset. Similar to [TFTP Boot](https://attack.mitre.org/techniques/T1542/005), an adversary may upgrade the ROMMON image locally or remotely (for example, through TFTP) with adversary code and restart the device in order to overwrite the existing ROMMON image. This provides adversaries with the means to update the ROMMON to gain persistence on a system in a way that may be difficult to detect.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Network

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Network intrusion detection and prevention systems that use network signatures to identify traffic for specific protocols, such as TFTP, can be used to mitigate activity at the network level. Signatures are often for unique indicators within protocols and may be based on the specific technique used by a particular adversary or tool, and will likely be different across various network configurations.   |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Boot Integrity\|M1046]] | Boot Integrity | Enable secure boot features to validate the digital signature of the boot environment and system image using a special purpose hardware device. If the validation check fails, the device will fail to boot preventing loading of unauthorized software. (Citation: Cisco IOS Software Integrity Assurance - Secure Boot)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Periodically check the integrity of system image to ensure it has not been modified. (Citation: Cisco IOS Software Integrity Assurance - Image File Integrity) (Citation: Cisco IOS Software Integrity Assurance - Image File Verification) (Citation: Cisco IOS Software Integrity Assurance - Change Control)  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1542/004
- Cisco Synful Knock Evolution: https://blogs.cisco.com/security/evolution-of-attacks-on-cisco-ios-devices
- Cisco Blog Legacy Device Attacks: https://community.cisco.com/t5/security-blogs/attackers-continue-to-target-legacy-devices/ba-p/4169954
