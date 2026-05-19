---
alias: T1602.002
---

## T1602.002

Adversaries may access network configuration files to collect sensitive data about the device and the network. The network configuration is a file containing parameters that determine the operation of the device. The device typically stores an in-memory copy of the configuration while operating, and a separate configuration on non-volatile storage to load after device reset. Adversaries can inspect the configuration files to reveal information about the target network and its layout, the network device and its software, or identifying legitimate accounts and credentials for later use.

Adversaries can use common management tools and protocols, such as Simple Network Management Protocol (SNMP) and Smart Install (SMI), to access network configuration files.(Citation: US-CERT TA18-106A Network Infrastructure Devices 2018)(Citation: Cisco Blog Legacy Device Attacks) These tools may be used to query specific data from a configuration repository or configure the device to export the configuration for later analysis. 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Collection]] (TA0009)

### Platforms
- Network

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Configure intrusion prevention devices to detect SNMP queries and commands from unauthorized sources. Create signatures to detect Smart Install (SMI) usage from sources other than trusted director.(Citation: US-CERT TA18-106A Network Infrastructure Devices 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Filter Network Traffic\|M1037]] | Filter Network Traffic | Apply extended ACLs to block unauthorized protocols outside the trusted network.(Citation: US-CERT TA17-156A SNMP Abuse 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Network Segmentation\|M1030]] | Network Segmentation | Segregate SNMP traffic on a separate management network.(Citation: US-CERT TA17-156A SNMP Abuse 2017)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Allowlist MIB objects and implement SNMP views. Disable Smart Install (SMI) if not used.(Citation: Cisco Securing SNMP)(Citation: US-CERT TA18-106A Network Infrastructure Devices 2018)  |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Update Software\|M1051]] | Update Software | Keep system images and software updated and migrate to SNMPv3.(Citation: Cisco Blog Legacy Device Attacks) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Configure SNMPv3 to use the highest level of security (authPriv) available.(Citation: US-CERT TA17-156A SNMP Abuse 2017)  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1602/002
- US-CERT TA18-106A Network Infrastructure Devices 2018: https://us-cert.cisa.gov/ncas/alerts/TA18-106A
- Cisco Blog Legacy Device Attacks: https://community.cisco.com/t5/security-blogs/attackers-continue-to-target-legacy-devices/ba-p/4169954
- US-CERT TA18-068A 2018: https://www.us-cert.gov/ncas/alerts/TA18-086A
