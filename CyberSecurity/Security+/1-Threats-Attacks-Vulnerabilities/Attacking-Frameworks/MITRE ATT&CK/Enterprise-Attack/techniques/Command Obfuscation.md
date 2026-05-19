---
alias: T1027.010
---

## T1027.010

Adversaries may obfuscate content during command execution to impede detection. Command-line obfuscation is a method of making strings and patterns within commands and scripts more difficult to signature and analyze. This type of obfuscation can be included within commands executed by delivered payloads (e.g., [Phishing](https://attack.mitre.org/techniques/T1566) and [Drive-by Compromise](https://attack.mitre.org/techniques/T1189)) or interactively via [Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059).(Citation: Akamai JS)(Citation: Malware Monday VBE)

For example, adversaries may abuse syntax that utilizes various symbols and escape characters (such as spacing,  `^`, `+`. `$`, and `%`) to make commands difficult to analyze while maintaining the same intended functionality.(Citation: RC PowerShell) Many languages support built-in obfuscation in the form of base64 or URL encoding.(Citation: Microsoft PowerShellB64) Adversaries may also manually implement command obfuscation via string splitting (`“Wor”+“d.Application”`), order and casing of characters (`rev <<<'dwssap/cte/ tac'`), globing (`mkdir -p '/tmp/:&$NiA'`), as well as various tricks involving passing strings through tokens/environment variables/input streams.(Citation: Bashfuscator Command Obfuscators)(Citation: FireEye Obfuscation June 2017)

Adversaries may also use tricks such as directory traversals to obfuscate references to the binary being invoked by a command (`C:\voi\pcw\..\..\Windows\tei\qs\k\..\..\..\system32\erool\..\wbem\wg\je\..\..\wmic.exe shadowcopy delete`).(Citation: Twitter Richard WMIC)

Tools such as <code>Invoke-Obfuscation</code> and <code>Invoke-DOSfucation</code> have also been used to obfuscate commands.(Citation: Invoke-DOSfuscation)(Citation: Invoke-Obfuscation)


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
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | On Windows 10+, enable Attack Surface Reduction (ASR) rules to block execution of potentially obfuscated scripts.(Citation: Microsoft ASR Obfuscation) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Antivirus／Antimalware\|M1049]] | Antivirus／Antimalware | Consider utilizing the Antimalware Scan Interface (AMSI) on Windows 10+ to analyze commands after being processed/interpreted.  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1027/010
- Twitter Richard WMIC: https://twitter.com/rfackroyd/status/1639136000755765254
- Invoke-Obfuscation: https://github.com/danielbohannon/Invoke-Obfuscation
- Invoke-DOSfuscation: https://github.com/danielbohannon/Invoke-DOSfuscation
- FireEye Obfuscation June 2017: https://web.archive.org/web/20170923102302/https://www.fireeye.com/blog/threat-research/2017/06/obfuscation-in-the-wild.html
- Malware Monday VBE: https://bromiley.medium.com/malware-monday-vbscript-and-vbe-files-292252c1a16
- Akamai JS: https://www.akamai.com/blog/security/catch-me-if-you-can-javascript-obfuscation
- Bashfuscator Command Obfuscators: https://bashfuscator.readthedocs.io/en/latest/Mutators/command_obfuscators/index.html
- Microsoft PowerShellB64: https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1#-encodedcommand-base64encodedcommand
- RC PowerShell: https://redcanary.com/threat-detection-report/techniques/powershell/
