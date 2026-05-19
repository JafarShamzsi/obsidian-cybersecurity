---
alias: T1499.003
---

## T1499.003

Adversaries may target resource intensive features of applications to cause a denial of service (DoS), denying availability to those applications. For example, specific features in web applications may be highly resource intensive. Repeated requests to those features may be able to exhaust system resources and deny access to the application or the server itself.(Citation: Arbor AnnualDoSreport Jan 2018)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Impact]] (TA0040)

### Platforms
- Windows
- Azure AD
- Office 365
- SaaS
- IaaS
- Linux
- macOS
- Google Workspace

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Filter Network Traffic\|M1037]] | Filter Network Traffic | Leverage services provided by Content Delivery Networks (CDN) or providers specializing in DoS mitigations to filter traffic upstream from services.(Citation: CERT-EU DDoS March 2017) Filter boundary traffic by blocking source addresses sourcing the attack, blocking ports that are being targeted, or blocking protocols being used for transport. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1499/003
- Arbor AnnualDoSreport Jan 2018: https://pages.arbornetworks.com/rs/082-KNA-087/images/13th_Worldwide_Infrastructure_Security_Report.pdf
- Cisco DoSdetectNetflow: https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/netflow/configuration/15-mt/nf-15-mt-book/nf-detct-analy-thrts.pdf
