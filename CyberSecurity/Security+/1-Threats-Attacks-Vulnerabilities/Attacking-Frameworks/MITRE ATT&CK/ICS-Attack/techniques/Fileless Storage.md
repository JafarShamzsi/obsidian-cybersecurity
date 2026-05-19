---
alias: T1027.011
---

## T1027.011

Adversaries may store data in "fileless" formats to conceal malicious activity from defenses. Fileless storage can be broadly defined as any format other than a file. Common examples of non-volatile fileless storage include the Windows Registry, event logs, or WMI repository.(Citation: Microsoft Fileless)(Citation: SecureList Fileless)

Similar to fileless in-memory behaviors such as [Reflective Code Loading](https://attack.mitre.org/techniques/T1620) and [Process Injection](https://attack.mitre.org/techniques/T1055), fileless data storage may remain undetected by anti-virus and other endpoint security tools that can only access specific file formats from disk storage.

Adversaries may use fileless storage to conceal various types of stored data, including payloads/shellcode (potentially being used as part of [Persistence](https://attack.mitre.org/tactics/TA0003)) and collected data not yet exfiltrated from the victim (e.g., [Local Data Staging](https://attack.mitre.org/techniques/T1074/001)). Adversaries also often encrypt, encode, splice, or otherwise obfuscate this fileless data when stored.

Some forms of fileless storage activity may indirectly create artifacts in the file system, but in central and otherwise difficult to inspect formats such as the WMI (e.g., `%SystemRoot%\System32\Wbem\Repository`) or Registry (e.g., `%SystemRoot%\System32\Config`) physical files.(Citation: Microsoft Fileless) 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Consider periodic review of common fileless storage locations (such as the Registry or WMI repository) to potentially identify abnormal and malicious data. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1027/011
- SecureList Fileless: https://securelist.com/a-new-secret-stash-for-fileless-malware/106393/
- Microsoft Fileless: https://learn.microsoft.com/microsoft-365/security/intelligence/fileless-threats
