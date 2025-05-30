---
alias: T1056.004
---

## T1056.004

Adversaries may hook into Windows application programming interface (API) functions to collect user credentials. Malicious hooking mechanisms may capture API calls that include parameters that reveal user authentication credentials.(Citation: Microsoft TrojanSpy:Win32/Ursnif.gen!I Sept 2017) Unlike [Keylogging](https://attack.mitre.org/techniques/T1056/001),  this technique focuses specifically on API functions that include parameters that reveal user credentials. Hooking involves redirecting calls to these functions and can be implemented via:

* **Hooks procedures**, which intercept and execute designated code in response to events such as messages, keystrokes, and mouse inputs.(Citation: Microsoft Hook Overview)(Citation: Elastic Process Injection July 2017)
* **Import address table (IAT) hooking**, which use modifications to a process’s IAT, where pointers to imported API functions are stored.(Citation: Elastic Process Injection July 2017)(Citation: Adlice Software IAT Hooks Oct 2014)(Citation: MWRInfoSecurity Dynamic Hooking 2015)
* **Inline hooking**, which overwrites the first bytes in an API function to redirect code flow.(Citation: Elastic Process Injection July 2017)(Citation: HighTech Bridge Inline Hooking Sept 2011)(Citation: MWRInfoSecurity Dynamic Hooking 2015)



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Collection]] (TA0009)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows

### Permissions Required
- Administrator
- SYSTEM

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1056/004
- Microsoft TrojanSpy:Win32/Ursnif.gen!I Sept 2017: https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?Name=TrojanSpy:Win32/Ursnif.gen!I&threatId=-2147336918
- Microsoft Hook Overview: https://msdn.microsoft.com/library/windows/desktop/ms644959.aspx
- Elastic Process Injection July 2017: https://www.endgame.com/blog/technical-blog/ten-process-injection-techniques-technical-survey-common-and-trending-process
- Adlice Software IAT Hooks Oct 2014: https://www.adlice.com/userland-rootkits-part-1-iat-hooks/
- MWRInfoSecurity Dynamic Hooking 2015: https://www.mwrinfosecurity.com/our-thinking/dynamic-hooking-techniques-user-mode/
- HighTech Bridge Inline Hooking Sept 2011: https://www.exploit-db.com/docs/17802.pdf
- Volatility Detecting Hooks Sept 2012: https://volatility-labs.blogspot.com/2012/09/movp-31-detecting-malware-hooks-in.html
- PreKageo Winhook Jul 2011: https://github.com/prekageo/winhook
- Jay GetHooks Sept 2011: https://github.com/jay/gethooks
- Zairon Hooking Dec 2006: https://zairon.wordpress.com/2006/12/06/any-application-defined-hook-procedure-on-my-machine/
- EyeofRa Detecting Hooking June 2017: https://eyeofrablog.wordpress.com/2017/06/27/windows-keylogger-part-2-defense-against-user-land/
- GMER Rootkits: http://www.gmer.net/
- Microsoft Process Snapshot: https://msdn.microsoft.com/library/windows/desktop/ms686701.aspx
- StackExchange Hooks Jul 2012: https://security.stackexchange.com/questions/17904/what-are-the-methods-to-find-hooked-functions-and-apis
