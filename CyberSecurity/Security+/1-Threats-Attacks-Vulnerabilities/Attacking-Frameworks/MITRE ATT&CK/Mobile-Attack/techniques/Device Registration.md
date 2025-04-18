---
alias: T1098.005
---

## T1098.005

Adversaries may register a device to an adversary-controlled account. Devices may be registered in a multifactor authentication (MFA) system, which handles authentication to the network, or in a device management system, which handles device access and compliance.

MFA systems, such as Duo or Okta, allow users to associate devices with their accounts in order to complete MFA requirements. An adversary that compromises a user’s credentials may enroll a new device in order to bypass initial MFA requirements and gain persistent access to a network.(Citation: CISA MFA PrintNightmare)(Citation: DarkReading FireEye SolarWinds) In some cases, the MFA self-enrollment process may require only a username and password to enroll the account's first device or to enroll a device to an inactive account. (Citation: Mandiant APT29 Microsoft 365 2022)

Similarly, an adversary with existing access to a network may register a device to Azure AD and/or its device management system, Microsoft Intune, in order to access sensitive data or resources while bypassing conditional access policies.(Citation: AADInternals - Device Registration)(Citation: AADInternals - Conditional Access Bypass)(Citation: Microsoft DEV-0537) 

Devices registered in Azure AD may be able to conduct [Internal Spearphishing](https://attack.mitre.org/techniques/T1534) campaigns via intra-organizational emails, which are less likely to be treated as suspicious by the email client.(Citation: Microsoft - Device Registration) Additionally, an adversary may be able to perform a [Service Exhaustion Flood](https://attack.mitre.org/techniques/T1499/002) on an Azure AD tenant by registering a large number of devices.(Citation: AADInternals - BPRT)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Azure AD
- Windows
- SaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Require multi-factor authentication to register devices in Azure AD.(Citation: Microsoft - Device Registration) Configure multi-factor authentication systems to disallow enrolling new devices for inactive accounts.(Citation: CISA MFA PrintNightmare) When first enrolling MFA, use conditional access policies to restrict device enrollment to trusted locations or devices, and consider using temporary access passes as an initial MFA solution to enroll a device.(Citation: Mandiant APT29 Microsoft 365 2022) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1098/005
- CISA MFA PrintNightmare: https://www.cisa.gov/uscert/ncas/alerts/aa22-074a
- Mandiant APT29 Microsoft 365 2022: https://www.mandiant.com/resources/blog/apt29-continues-targeting-microsoft
- AADInternals - Conditional Access Bypass: https://o365blog.com/post/mdm
- AADInternals - BPRT: https://o365blog.com/post/bprt/
- AADInternals - Device Registration: https://o365blog.com/post/devices/
- DarkReading FireEye SolarWinds: https://www.darkreading.com/threat-intelligence/fireeye-s-mandia-severity-zero-alert-led-to-discovery-of-solarwinds-attack
- Microsoft - Device Registration: https://www.microsoft.com/security/blog/2022/01/26/evolved-phishing-device-registration-trick-adds-to-phishers-toolbox-for-victims-without-mfa
- Microsoft DEV-0537: https://www.microsoft.com/security/blog/2022/03/22/dev-0537-criminal-actor-targeting-organizations-for-data-exfiltration-and-destruction/
