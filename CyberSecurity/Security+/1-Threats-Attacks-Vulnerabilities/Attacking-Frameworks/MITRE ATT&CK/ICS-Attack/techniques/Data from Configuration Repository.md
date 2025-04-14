---
alias: T1602
---

## T1602

Adversaries may collect data related to managed devices from configuration repositories. Configuration repositories are used by management systems in order to configure, manage, and control data on remote systems. Configuration repositories may also facilitate remote access and administration of devices.

Adversaries may target these repositories in order to collect large quantities of sensitive system administration data. Data from configuration repositories may be exposed by various protocols and software and can store a wide variety of data, much of which may align with adversary Discovery objectives.(Citation: US-CERT-TA18-106A)(Citation: US-CERT TA17-156A SNMP Abuse 2017)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Collection]] (TA0009)

### Platforms
- Network

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Configure intrusion prevention devices to detect SNMP queries and commands from unauthorized sources.(Citation: US-CERT-TA18-106A) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Filter Network Traffic\|M1037]] | Filter Network Traffic | Apply extended ACLs to block unauthorized protocols outside the trusted network.(Citation: US-CERT TA17-156A SNMP Abuse 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Network Segmentation\|M1030]] | Network Segmentation | Segregate SNMP traffic on a separate management network.(Citation: US-CERT TA17-156A SNMP Abuse 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Allowlist MIB objects and implement SNMP views.(Citation: Cisco Securing SNMP) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Update Software\|M1051]] | Update Software | Keep system images and software updated and migrate to SNMPv3.(Citation: Cisco Blog Legacy Device Attacks) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Configure SNMPv3 to use the highest level of security (authPriv) available.(Citation: US-CERT TA17-156A SNMP Abuse 2017) |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Network Device Configuration Dump\|T1602.002]] | Network Device Configuration Dump |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/SNMP (MIB Dump)\|T1602.001]] | SNMP (MIB Dump) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1602
- Cisco Advisory SNMP v3 Authentication Vulnerabilities: https://tools.cisco.com/security/center/content/CiscoAppliedMitigationBulletin/cisco-amb-20080610-SNMPv3
- US-CERT TA17-156A SNMP Abuse 2017: https://us-cert.cisa.gov/ncas/alerts/TA17-156A
- US-CERT-TA18-106A: https://www.us-cert.gov/ncas/alerts/TA18-106A
