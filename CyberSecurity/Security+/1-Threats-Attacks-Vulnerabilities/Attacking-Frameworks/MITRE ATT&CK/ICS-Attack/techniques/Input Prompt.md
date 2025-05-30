---
alias: T1141
---

## T1141

When programs are executed that need additional privileges than are present in the current user context, it is common for the operating system to prompt the user for proper credentials to authorize the elevated privileges for the task (ex: [Bypass User Account Control](https://attack.mitre.org/techniques/T1088)).

Adversaries may mimic this functionality to prompt users for credentials with a seemingly legitimate prompt for a number of reasons that mimic normal usage, such as a fake installer requiring additional access or a fake malware removal suite.(Citation: OSX Malware Exploits MacKeeper) This type of prompt can be used to collect credentials via various languages such as [AppleScript](https://attack.mitre.org/techniques/T1155)(Citation: LogRhythm Do You Trust Oct 2014)(Citation: OSX Keydnap malware) and [PowerShell](https://attack.mitre.org/techniques/T1086)(Citation: LogRhythm Do You Trust Oct 2014)(Citation: Enigma Phishing for Credentials Jan 2015).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- macOS
- Windows

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Training\|M1017]] | User Training | Use user training as a way to bring awareness and raise suspicion for potentially malicious events (ex: Office documents prompting for credentials). |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1141
- capec: https://capec.mitre.org/data/definitions/569.html
- OSX Malware Exploits MacKeeper: https://baesystemsai.blogspot.com/2015/06/new-mac-os-malware-exploits-mackeeper.html
- LogRhythm Do You Trust Oct 2014: https://logrhythm.com/blog/do-you-trust-your-computer/
- OSX Keydnap malware: https://www.welivesecurity.com/2016/07/06/new-osxkeydnap-malware-hungry-credentials/
- Enigma Phishing for Credentials Jan 2015: https://enigma0x3.net/2015/01/21/phishing-for-credentials-if-you-want-it-just-ask/
