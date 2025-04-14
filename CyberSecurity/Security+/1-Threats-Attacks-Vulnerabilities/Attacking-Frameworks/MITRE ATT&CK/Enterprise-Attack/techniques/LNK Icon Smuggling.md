---
alias: T1027.012
---

## T1027.012

Adversaries may smuggle commands to download malicious payloads past content filters by hiding them within otherwise seemingly benign windows shortcut files. Windows shortcut files (.LNK) include many metadata fields, including an icon location field (also known as the `IconEnvironmentDataBlock`) designed to specify the path to an icon file that is to be displayed for the LNK file within a host directory. 

Adversaries may abuse this LNK metadata to download malicious payloads. For example, adversaries have been observed using LNK files as phishing payloads to deliver malware. Once invoked (e.g., [Malicious File](https://attack.mitre.org/techniques/T1204/002)), payloads referenced via external URLs within the LNK icon location field may be downloaded. These files may also then be invoked by [Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059)/[System Binary Proxy Execution](https://attack.mitre.org/techniques/T1218) arguments within the target path field of the LNK.(Citation: Unprotect Shortcut)(Citation: Booby Trap Shortcut 2017)

LNK Icon Smuggling may also be utilized post compromise, such as malicious scripts executing an LNK on an infected host to download additional malicious payloads. 



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | On Windows 10, enable Attack Surface Reduction (ASR) rules to prevent execution of potentially obfuscated scripts or payloads. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Antivirus／Antimalware\|M1049]] | Antivirus／Antimalware | Use signatures or heuristics to detect malicious LNK and subsequently downloaded files. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1027/012
- Unprotect Shortcut: https://unprotect.it/technique/shortcut-hiding/
- Booby Trap Shortcut 2017: https://www.uperesia.com/booby-trapped-shortcut
