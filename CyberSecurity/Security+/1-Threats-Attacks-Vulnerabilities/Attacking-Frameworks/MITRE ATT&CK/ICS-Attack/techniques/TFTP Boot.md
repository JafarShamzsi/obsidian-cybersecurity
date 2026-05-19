---
alias: T1542.005
---

## T1542.005

Adversaries may abuse netbooting to load an unauthorized network device operating system from a Trivial File Transfer Protocol (TFTP) server. TFTP boot (netbooting) is commonly used by network administrators to load configuration-controlled network device images from a centralized management server. Netbooting is one option in the boot sequence and can be used to centralize, manage, and control device images.

Adversaries may manipulate the configuration on the network device specifying use of a malicious TFTP server, which may be used in conjunction with [Modify System Image](https://attack.mitre.org/techniques/T1601) to load a modified image on device startup or reset. The unauthorized image allows adversaries to modify device configuration, add malicious capabilities to the device, and introduce backdoors to maintain control of the network device while minimizing detection through use of a standard functionality. This technique is similar to [ROMMONkit](https://attack.mitre.org/techniques/T1542/004) and may result in the network device running a modified image. (Citation: Cisco Blog Legacy Device Attacks)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Network

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Network intrusion detection and prevention systems that use network signatures to identify traffic for specific protocols, such as TFTP, can be used to mitigate activity at the network level. Signatures are often for unique indicators within protocols and may be based on the specific technique used by a particular adversary or tool, and will likely be different across various network configurations.  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Limit Access to Resource Over Network\|M1035]] | Limit Access to Resource Over Network | Restrict use of protocols without encryption or authentication mechanisms. Limit access to administrative and management interfaces from untrusted network sources.  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Operating System Configuration\|M1028]] | Operating System Configuration | Follow vendor device hardening best practices to disable unnecessary and unused features and services, avoid using default configurations and passwords, and introduce logging and auditing for detection. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Boot Integrity\|M1046]] | Boot Integrity | Enable secure boot features to validate the digital signature of the boot environment and system image using a special purpose hardware device. If the validation check fails, the device will fail to boot preventing loading of unauthorized software. (Citation: Cisco IOS Software Integrity Assurance - Secure Boot)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Use of Authentication, Authorization, and Accounting (AAA) systems will limit actions administrators can perform and provide a history of user actions to detect unauthorized use and abuse. TACACS+ can keep control over which commands administrators are permitted to use through the configuration of authentication and command authorization. (Citation: Cisco IOS Software Integrity Assurance - AAA) (Citation: Cisco IOS Software Integrity Assurance - TACACS) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Periodically check the integrity of the running configuration and system image to ensure they have not been modified. (Citation: Cisco IOS Software Integrity Assurance - Image File Verification) (Citation: Cisco IOS Software Integrity Assurance - Image File Integrity) (Citation: Cisco IOS Software Integrity Assurance - Change Control)  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1542/005
- Cisco Blog Legacy Device Attacks: https://community.cisco.com/t5/security-blogs/attackers-continue-to-target-legacy-devices/ba-p/4169954
- Cisco IOS Software Integrity Assurance - Secure Boot: https://tools.cisco.com/security/center/resources/integrity_assurance.html#35
- Cisco IOS Software Integrity Assurance - Image File Verification: https://tools.cisco.com/security/center/resources/integrity_assurance.html#7
- Cisco IOS Software Integrity Assurance - Run-Time Memory Verification: https://tools.cisco.com/security/center/resources/integrity_assurance.html#13
- Cisco IOS Software Integrity Assurance - Command History: https://tools.cisco.com/security/center/resources/integrity_assurance.html#23
- Cisco IOS Software Integrity Assurance - Boot Information: https://tools.cisco.com/security/center/resources/integrity_assurance.html#26
