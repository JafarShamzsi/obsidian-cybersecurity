---
alias: T1614.001
---

## T1614.001

Adversaries may attempt to gather information about the system language of a victim in order to infer the geographical location of that host. This information may be used to shape follow-on behaviors, including whether the adversary infects the target and/or attempts specific actions. This decision may be employed by malware developers and operators to reduce their risk of attracting the attention of specific law enforcement agencies or prosecution/scrutiny from other entities.(Citation: Malware System Language Check)

There are various sources of data an adversary could use to infer system language, such as system defaults and keyboard layouts. Specific checks will vary based on the target and/or adversary, but may involve behaviors such as [Query Registry](https://attack.mitre.org/techniques/T1012) and calls to [Native API](https://attack.mitre.org/techniques/T1106) functions.(Citation: CrowdStrike Ryuk January 2019) 

For example, on a Windows system adversaries may attempt to infer the language of a system by querying the registry key <code>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\Language</code> or parsing the outputs of Windows API functions <code>GetUserDefaultUILanguage</code>, <code>GetSystemDefaultUILanguage</code>, <code>GetKeyboardLayoutList</code> and <code>GetUserDefaultLangID</code>.(Citation: Darkside Ransomware Cybereason)(Citation: Securelist JSWorm)(Citation: SecureList SynAck Doppelgänging May 2018)

On a macOS or Linux system, adversaries may query <code>locale</code> to retrieve the value of the <code>$LANG</code> environment variable.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows
- Linux
- macOS

### Permissions Required
- User

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1614/001
- Malware System Language Check: https://www.welivesecurity.com/2009/01/15/malware-trying-to-avoid-some-countries/
- CrowdStrike Ryuk January 2019: https://www.crowdstrike.com/blog/big-game-hunting-with-ryuk-another-lucrative-targeted-ransomware/
- Darkside Ransomware Cybereason: https://www.cybereason.com/blog/cybereason-vs-darkside-ransomware
- Securelist JSWorm: https://securelist.com/evolution-of-jsworm-ransomware/102428/
- SecureList SynAck Doppelgänging May 2018: https://securelist.com/synack-targeted-ransomware-uses-the-doppelganging-technique/85431/
