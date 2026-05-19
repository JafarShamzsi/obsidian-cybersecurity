---
alias: T1173
---

## T1173

Windows Dynamic Data Exchange (DDE) is a client-server protocol for one-time and/or continuous inter-process communication (IPC) between applications. Once a link is established, applications can autonomously exchange transactions consisting of strings, warm data links (notifications when a data item changes), hot data links (duplications of changes to a data item), and requests for command execution.

Object Linking and Embedding (OLE), or the ability to link data between documents, was originally implemented through DDE. Despite being superseded by COM, DDE may be enabled in Windows 10 and most of Microsoft Office 2016 via Registry keys. (Citation: BleepingComputer DDE Disabled in Word Dec 2017) (Citation: Microsoft ADV170021 Dec 2017) (Citation: Microsoft DDE Advisory Nov 2017)

Adversaries may use DDE to execute arbitrary commands. Microsoft Office documents can be poisoned with DDE commands (Citation: SensePost PS DDE May 2016) (Citation: Kettle CSV DDE Aug 2014), directly or through embedded files (Citation: Enigma Reviving DDE Jan 2018), and used to deliver execution via phishing campaigns or hosted Web content, avoiding the use of Visual Basic for Applications (VBA) macros. (Citation: SensePost MacroLess DDE Oct 2017) DDE could also be leveraged by an adversary operating on a compromised machine who does not have direct access to command line execution.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)

### Platforms
- Windows

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | On Windows 10, enable Attack Surface Reduction (ASR) rules to prevent DDE attacks and spawning of child processes from Office programs. (Citation: Microsoft ASR Nov 2017) (Citation: Enigma Reviving DDE Jan 2018) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Consider disabling embedded files in Office programs, such as OneNote, that do not work with Protected View.(Citation: Enigma Reviving DDE Jan 2018)(Citation: GitHub Disable DDEAUTO Oct 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Application Isolation and Sandboxing\|M1048]] | Application Isolation and Sandboxing | Ensure Protected View is enabled.(Citation: Microsoft Protected View) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Registry keys specific to Microsoft Office feature control security can be set to disable automatic DDE/OLE execution. (Citation: Microsoft DDE Advisory Nov 2017) (Citation: BleepingComputer DDE Disabled in Word Dec 2017) (Citation: GitHub Disable DDEAUTO Oct 2017) Microsoft also created, and enabled by default, Registry keys to completely disable DDE execution in Word and Excel. (Citation: Microsoft ADV170021 Dec 2017) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1173
- BleepingComputer DDE Disabled in Word Dec 2017: https://www.bleepingcomputer.com/news/microsoft/microsoft-disables-dde-feature-in-word-to-prevent-further-malware-attacks/
- Microsoft ADV170021 Dec 2017: https://portal.msrc.microsoft.com/security-guidance/advisory/ADV170021
- Microsoft DDE Advisory Nov 2017: https://technet.microsoft.com/library/security/4053440
- SensePost PS DDE May 2016: https://sensepost.com/blog/2016/powershell-c-sharp-and-dde-the-power-within/
- Kettle CSV DDE Aug 2014: https://www.contextis.com/blog/comma-separated-vulnerabilities
- Enigma Reviving DDE Jan 2018: https://posts.specterops.io/reviving-dde-using-onenote-and-excel-for-code-execution-d7226864caee
- SensePost MacroLess DDE Oct 2017: https://sensepost.com/blog/2017/macro-less-code-exec-in-msword/
- NVisio Labs DDE Detection Oct 2017: https://blog.nviso.be/2017/10/11/detecting-dde-in-ms-office-documents/
