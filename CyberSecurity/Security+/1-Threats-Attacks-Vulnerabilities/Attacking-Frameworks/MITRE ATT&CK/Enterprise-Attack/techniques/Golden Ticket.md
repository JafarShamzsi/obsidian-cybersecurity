---
alias: T1558.001
---

## T1558.001

Adversaries who have the KRBTGT account password hash may forge Kerberos ticket-granting tickets (TGT), also known as a golden ticket.(Citation: AdSecurity Kerberos GT Aug 2015) Golden tickets enable adversaries to generate authentication material for any account in Active Directory.(Citation: CERT-EU Golden Ticket Protection) 

Using a golden ticket, adversaries are then able to request ticket granting service (TGS) tickets, which enable access to specific resources. Golden tickets require adversaries to interact with the Key Distribution Center (KDC) in order to obtain TGS.(Citation: ADSecurity Detecting Forged Tickets)

The KDC service runs all on domain controllers that are part of an Active Directory domain. KRBTGT is the Kerberos Key Distribution Center (KDC) service account and is responsible for encrypting and signing all Kerberos tickets.(Citation: ADSecurity Kerberos and KRBTGT) The KRBTGT password hash may be obtained using [OS Credential Dumping](https://attack.mitre.org/techniques/T1003) and privileged access to a domain controller.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Limit domain admin account permissions to domain controllers and limited servers. Delegate other admin functions to separate accounts. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Active Directory Configuration\|M1015]] | Active Directory Configuration | For containing the impact of a previously generated golden ticket, reset the built-in KRBTGT account password twice, which will invalidate any existing golden tickets that have been created with the KRBTGT hash and other Kerberos tickets derived from it. For each domain, change the KRBTGT account password once, force replication, and then change the password a second time. Consider rotating the KRBTGT account password every 180 days.(Citation: STIG krbtgt reset) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1558/001
- AdSecurity Kerberos GT Aug 2015: https://adsecurity.org/?p=1640
- CERT-EU Golden Ticket Protection: https://cert.europa.eu/static/WhitePapers/UPDATED%20-%20CERT-EU_Security_Whitepaper_2014-007_Kerberos_Golden_Ticket_Protection_v1_4.pdf
- ADSecurity Detecting Forged Tickets: https://adsecurity.org/?p=1515
- ADSecurity Kerberos and KRBTGT: https://adsecurity.org/?p=483
- Stealthbits Detect PtT 2019: https://blog.stealthbits.com/detect-pass-the-ticket-attacks
- Microsoft Kerberos Golden Ticket: https://gallery.technet.microsoft.com/scriptcenter/Kerberos-Golden-Ticket-b4814285
