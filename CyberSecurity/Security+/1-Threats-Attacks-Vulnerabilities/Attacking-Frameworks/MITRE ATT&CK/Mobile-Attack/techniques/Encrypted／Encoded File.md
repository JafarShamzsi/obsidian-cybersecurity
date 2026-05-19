---
alias: T1027.013
---

## T1027.013

Adversaries may encrypt or encode files to obfuscate strings, bytes, and other specific patterns to impede detection. Encrypting and/or encoding file content aims to conceal malicious artifacts within a file used in an intrusion. Many other techniques, such as [Software Packing](https://attack.mitre.org/techniques/T1027/002), [Steganography](https://attack.mitre.org/techniques/T1027/003), and [Embedded Payloads](https://attack.mitre.org/techniques/T1027/009), share this same broad objective. Encrypting and/or encoding files could lead to a lapse in detection of static signatures, only for this malicious content to be revealed (i.e., [Deobfuscate/Decode Files or Information](https://attack.mitre.org/techniques/T1140)) at the time of execution/use.

This type of file obfuscation can be applied to many file artifacts present on victim hosts, such as malware log/configuration and payload files.(Citation: File obfuscation) Files can be encrypted with a hardcoded or user-supplied key, as well as otherwise obfuscated using standard encoding/compression schemes such as Base64.

The entire content of a file may be obfuscated, or just specific functions or values (such as C2 addresses). Encryption and encoding may also be applied in redundant layers for additional protection.

For example, adversaries may abuse password-protected Word documents or self-extracting (SFX) archives as a method of encrypting/encoding a file such as a [Phishing](https://attack.mitre.org/techniques/T1566) payload. These files typically function by attaching the intended archived content to a decompressor stub that is executed when the file is invoked (e.g., [User Execution](https://attack.mitre.org/techniques/T1204)).(Citation: SFX - Encrypted/Encoded File) 

Adversaries may also abuse file-specific as well as custom encoding schemes. For example, Byte Order Mark (BOM) headers in text files may be abused to manipulate and obfuscate file content until [Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059) execution.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | On Windows 10+, enable Attack Surface Reduction (ASR) rules to block execution of potentially obfuscated scripts.(Citation: Obfuscated scripts)<br /><br />Security tools should be configured to analyze the encoding properties of files and detect anomalies that deviate from standard encoding practices. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Antivirus／Antimalware\|M1049]] | Antivirus／Antimalware | Anti-virus can be used to automatically detect and quarantine suspicious files, including those with high entropy measurements or with otherwise potentially malicious signs of obfuscation. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1027/013
- File obfuscation: https://www.crowdstrike.com/blog/shlayer-malvertising-campaigns-still-using-flash-update-disguise/
- SFX - Encrypted/Encoded File: https://www.crowdstrike.com/blog/self-extracting-archives-decoy-files-and-their-hidden-payloads/
