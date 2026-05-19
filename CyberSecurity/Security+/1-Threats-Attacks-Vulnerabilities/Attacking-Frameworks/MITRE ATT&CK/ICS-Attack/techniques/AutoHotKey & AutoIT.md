---
alias: T1059.010
---

## T1059.010

Adversaries may execute commands and perform malicious tasks using AutoIT and AutoHotKey automation scripts. AutoIT and AutoHotkey (AHK) are scripting languages that enable users to automate Windows tasks. These automation scripts can be used to perform a wide variety of actions, such as clicking on buttons, entering text, and opening and closing programs.(Citation: AutoIT)(Citation: AutoHotKey)

Adversaries may use AHK (`.ahk`) and AutoIT (`.au3`) scripts to execute malicious code on a victim's system. For example, adversaries have used for AHK to execute payloads and other modular malware such as keyloggers. Adversaries have also used custom AHK files containing embedded malware as [Phishing](https://attack.mitre.org/techniques/T1566) payloads.(Citation: Splunk DarkGate)

These scripts may also be compiled into self-contained executable payloads (`.exe`).(Citation: AutoIT)(Citation: AutoHotKey)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Use application control to prevent execution of `AutoIt3.exe`, `AutoHotkey.exe`, and other related features that may not be required for a given system or network to prevent potential misuse by adversaries. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1059/010
- AutoHotKey: https://www.autohotkey.com/docs/v1/Program.htm
- AutoIT: https://www.autoitscript.com/autoit3/docs/intro/running.htm
- Splunk DarkGate: https://www.splunk.com/en_us/blog/security/enter-the-gates-an-analysis-of-the-darkgate-autoit-loader.html
