---
alias: T1027.009
---

## T1027.009

Adversaries may embed payloads within other files to conceal malicious content from defenses. Otherwise seemingly benign files (such as scripts and executables) may be abused to carry and obfuscate malicious payloads and content. In some cases, embedded payloads may also enable adversaries to [Subvert Trust Controls](https://attack.mitre.org/techniques/T1553) by not impacting execution controls such as digital signatures and notarization tickets.(Citation: Sentinel Labs) 

Adversaries may embed payloads in various file formats to hide payloads.(Citation: Microsoft Learn) This is similar to [Steganography](https://attack.mitre.org/techniques/T1027/003), though does not involve weaving malicious content into specific bytes and patterns related to legitimate digital media formats.(Citation: GitHub PSImage) 

For example, adversaries have been observed embedding payloads within or as an overlay of an otherwise benign binary.(Citation: Securelist Dtrack2) Adversaries have also been observed nesting payloads (such as executables and run-only scripts) inside a file of the same format.(Citation: SentinelLabs reversing run-only applescripts 2021) 

Embedded content may also be used as [Process Injection](https://attack.mitre.org/techniques/T1055) payloads used to infect benign system processes.(Citation: Trend Micro) These embedded then injected payloads may be used as part of the modules of malware designed to provide specific features such as encrypting C2 communications in support of an orchestrator module. For example, an embedded module may be injected into default browsers, allowing adversaries to then communicate via the network.(Citation: Malware Analysis Report ComRAT)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- macOS
- Windows
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | On Windows 10, enable Attack Surface Reduction (ASR) rules to prevent execution of potentially obfuscated scripts.(Citation: win10_asr) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Antivirus／Antimalware\|M1049]] | Antivirus／Antimalware | Anti-virus can be used to automatically detect and quarantine suspicious files. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1027/009
- GitHub PSImage: https://github.com/peewpw/Invoke-PSImage
- Malware Analysis Report ComRAT: https://www.cisa.gov/uscert/ncas/analysis-reports/ar20-303a
- Trend Micro: https://www.trendmicro.com/en_us/research/20/e/netwalker-fileless-ransomware-injected-via-reflective-loading.html
- Securelist Dtrack2: https://securelist.com/my-name-is-dtrack/93338/
- Microsoft Learn: https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-shllink/c41e062d-f764-4f13-bd4f-ea812ab9a4d1
- SentinelLabs reversing run-only applescripts 2021: https://www.sentinelone.com/labs/fade-dead-adventures-in-reversing-malicious-run-only-applescripts/
- Sentinel Labs: https://www.sentinelone.com/labs/fade-dead-adventures-in-reversing-malicious-run-only-applescripts/
