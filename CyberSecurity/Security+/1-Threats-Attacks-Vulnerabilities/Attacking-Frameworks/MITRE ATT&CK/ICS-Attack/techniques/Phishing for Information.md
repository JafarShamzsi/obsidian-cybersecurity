---
alias: T1598
---

## T1598

Adversaries may send phishing messages to elicit sensitive information that can be used during targeting. Phishing for information is an attempt to trick targets into divulging information, frequently credentials or other actionable information. Phishing for information is different from [Phishing](https://attack.mitre.org/techniques/T1566) in that the objective is gathering data from the victim rather than executing malicious code.

All forms of phishing are electronically delivered social engineering. Phishing can be targeted, known as spearphishing. In spearphishing, a specific individual, company, or industry will be targeted by the adversary. More generally, adversaries can conduct non-targeted phishing, such as in mass credential harvesting campaigns.

Adversaries may also try to obtain information directly through the exchange of emails, instant messages, or other electronic conversation means.(Citation: ThreatPost Social Media Phishing)(Citation: TrendMictro Phishing)(Citation: PCMag FakeLogin)(Citation: Sophos Attachment)(Citation: GitHub Phishery) Victims may also receive phishing messages that direct them to call a phone number where the adversary attempts to collect confidential information.(Citation: Avertium callback phishing)

Phishing for information frequently involves social engineering techniques, such as posing as a source with a reason to collect information (ex: [Establish Accounts](https://attack.mitre.org/techniques/T1585) or [Compromise Accounts](https://attack.mitre.org/techniques/T1586)) and/or sending multiple, seemingly urgent messages. Another way to accomplish this is by forging or spoofing(Citation: Proofpoint-spoof) the identity of the sender which can be used to fool both the human recipient as well as automated security tools.(Citation: cyberproof-double-bounce) 

Phishing for information may also involve evasive techniques, such as removing or manipulating emails or metadata/headers from compromised accounts being abused to send messages (e.g., [Email Hiding Rules](https://attack.mitre.org/techniques/T1564/008)).(Citation: Microsoft OAuth Spam 2022)(Citation: Palo Alto Unit 42 VBA Infostealer 2014)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Reconnaissance]] (TA0043)

### Platforms
- PRE

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Training\|M1017]] | User Training | Users can be trained to identify social engineering techniques and spearphishing attempts. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Use anti-spoofing and email authentication mechanisms to filter messages based on validity checks of the sender domain (using SPF) and integrity of messages (using DKIM). Enabling these mechanisms within an organization (through policies such as DMARC) may enable recipients (intra-org and cross domain) to perform similar message filtering and validation.(Citation: Microsoft Anti Spoofing)(Citation: ACSC Email Spoofing) |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Link\|T1598.003]] | Spearphishing Link |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Voice\|T1598.004]] | Spearphishing Voice |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Attachment\|T1598.002]] | Spearphishing Attachment |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Spearphishing Service\|T1598.001]] | Spearphishing Service |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1598
- ACSC Email Spoofing: https://www.cyber.gov.au/sites/default/files/2019-03/spoof_email_sender_policy_framework.pdf
- Avertium callback phishing: https://www.avertium.com/resources/threat-reports/everything-you-need-to-know-about-callback-phishing
- TrendMictro Phishing: https://www.trendmicro.com/en_us/research/20/i/tricky-forms-of-phishing.html
- Sophos Attachment: https://nakedsecurity.sophos.com/2020/10/02/serious-security-phishing-without-links-when-phishers-bring-along-their-own-web-pages/
- cyberproof-double-bounce: https://blog.cyberproof.com/blog/double-bounced-attacks-with-email-spoofing-2022-trends
- PCMag FakeLogin: https://www.pcmag.com/news/hackers-try-to-phish-united-nations-staffers-with-fake-login-pages
- Microsoft Anti Spoofing: https://docs.microsoft.com/en-us/microsoft-365/security/office-365-security/anti-spoofing-protection?view=o365-worldwide
- Microsoft OAuth Spam 2022: https://www.microsoft.com/en-us/security/blog/2022/09/22/malicious-oauth-applications-used-to-compromise-email-servers-and-spread-spam/
- ThreatPost Social Media Phishing: https://threatpost.com/facebook-launching-pad-phishing-attacks/160351/
- Proofpoint-spoof: https://www.proofpoint.com/us/threat-reference/email-spoofing
- GitHub Phishery: https://github.com/ryhanson/phishery
- Palo Alto Unit 42 VBA Infostealer 2014: https://unit42.paloaltonetworks.com/examining-vba-initiated-infostealer-campaign/
