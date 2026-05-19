---
alias: T1621
---

## T1621

Adversaries may attempt to bypass multi-factor authentication (MFA) mechanisms and gain access to accounts by generating MFA requests sent to users.

Adversaries in possession of credentials to [Valid Accounts](https://attack.mitre.org/techniques/T1078) may be unable to complete the login process if they lack access to the 2FA or MFA mechanisms required as an additional credential and security control. To circumvent this, adversaries may abuse the automatic generation of push notifications to MFA services such as Duo Push, Microsoft Authenticator, Okta, or similar services to have the user grant access to their account. If adversaries lack credentials to victim accounts, they may also abuse automatic push notification generation when this option is configured for self-service password reset (SSPR).(Citation: Obsidian SSPR Abuse 2023)

In some cases, adversaries may continuously repeat login attempts in order to bombard users with MFA push notifications, SMS messages, and phone calls, potentially resulting in the user finally accepting the authentication request in response to “MFA fatigue.”(Citation: Russian 2FA Push Annoyance - Cimpanu)(Citation: MFA Fatigue Attacks - PortSwigger)(Citation: Suspected Russian Activity Targeting Government and Business Entities Around the Globe)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows
- Office 365
- Linux
- macOS
- IaaS
- SaaS
- Azure AD
- Google Workspace

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Training\|M1017]] | User Training | Train users to only accept 2FA/MFA requests from login attempts they initiated, to review source location of the login attempt prompting the 2FA/MFA requests, and to report suspicious/unsolicited prompts. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Multi-Factor Authentication\|M1032]] | Multi-factor Authentication | Implement more secure 2FA/MFA mechanisms in replacement of simple push or one-click 2FA/MFA options. For example, having users enter a one-time code provided by the login screen into the 2FA/MFA application or utilizing other out-of-band 2FA/MFA mechanisms (such as rotating code-based hardware tokens providing rotating codes that need an accompanying user pin) may be more secure. Furthermore, change default configurations and implement limits upon the maximum number of 2FA/MFA request prompts that can be sent to users in period of time.(Citation: MFA Fatigue Attacks - PortSwigger) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Account Use Policies\|M1036]] | Account Use Policies | Enable account restrictions to prevent login attempts, and the subsequent 2FA/MFA service requests, from being initiated from suspicious locations or when the source of the login attempts do not match the location of the 2FA/MFA smart device. Use conditional access policies to block logins from non-compliant devices or from outside defined organization IP ranges.(Citation: Microsoft Common Conditional Access Policies) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1621
- Russian 2FA Push Annoyance - Cimpanu: https://therecord.media/russian-hackers-bypass-2fa-by-annoying-victims-with-repeated-push-notifications/
- MFA Fatigue Attacks - PortSwigger: https://portswigger.net/daily-swig/mfa-fatigue-attacks-users-tricked-into-allowing-device-access-due-to-overload-of-push-notifications
- Suspected Russian Activity Targeting Government and Business Entities Around the Globe: https://www.mandiant.com/resources/russian-targeting-gov-business
- Obsidian SSPR Abuse 2023: https://www.obsidiansecurity.com/blog/behind-the-breach-self-service-password-reset-azure-ad/
