---
alias: T1218.002
---

## T1218.002

Adversaries may abuse control.exe to proxy execution of malicious payloads. The Windows Control Panel process binary (control.exe) handles execution of Control Panel items, which are utilities that allow users to view and adjust computer settings.

Control Panel items are registered executable (.exe) or Control Panel (.cpl) files, the latter are actually renamed dynamic-link library (.dll) files that export a <code>CPlApplet</code> function.(Citation: Microsoft Implementing CPL)(Citation: TrendMicro CPL Malware Jan 2014) For ease of use, Control Panel items typically include graphical menus available to users after being registered and loaded into the Control Panel.(Citation: Microsoft Implementing CPL) Control Panel items can be executed directly from the command line, programmatically via an application programming interface (API) call, or by simply double-clicking the file.(Citation: Microsoft Implementing CPL) (Citation: TrendMicro CPL Malware Jan 2014)(Citation: TrendMicro CPL Malware Dec 2013)

Malicious Control Panel items can be delivered via [Phishing](https://attack.mitre.org/techniques/T1566) campaigns(Citation: TrendMicro CPL Malware Jan 2014)(Citation: TrendMicro CPL Malware Dec 2013) or executed as part of multi-stage malware.(Citation: Palo Alto Reaver Nov 2017) Control Panel items, specifically CPL files, may also bypass application and/or file extension allow lists.

Adversaries may also rename malicious DLL files (.dll) with Control Panel file extensions (.cpl) and register them to <code>HKCU\Software\Microsoft\Windows\CurrentVersion\Control Panel\Cpls</code>. Even when these registered DLLs do not comply with the CPL file specification and do not export <code>CPlApplet</code> functions, they are loaded and executed through its <code>DllEntryPoint</code> when Control Panel is executed. CPL files not exporting <code>CPlApplet</code> are not directly executable.(Citation: ESET InvisiMole June 2020)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required
- User
- Administrator
- SYSTEM

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Identify and block potentially malicious and unknown .cpl files by using application control (Citation: Beechey 2010) tools, like Windows Defender Application Control(Citation: Microsoft Windows Defender Application Control), AppLocker, (Citation: Windows Commands JPCERT) (Citation: NSA MS AppLocker) or Software Restriction Policies (Citation: Corio 2008) where appropriate. (Citation: TechNet Applocker vs SRP) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Restrict storage and execution of Control Panel items to protected directories, such as <code>C:\Windows</code>, rather than user directories. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1218/002
- Microsoft Implementing CPL: https://msdn.microsoft.com/library/windows/desktop/cc144185.aspx
- TrendMicro CPL Malware Jan 2014: https://www.trendmicro.de/cloud-content/us/pdfs/security-intelligence/white-papers/wp-cpl-malware.pdf
- TrendMicro CPL Malware Dec 2013: https://blog.trendmicro.com/trendlabs-security-intelligence/control-panel-files-used-as-malicious-attachments/
- Palo Alto Reaver Nov 2017: https://researchcenter.paloaltonetworks.com/2017/11/unit42-new-malware-with-ties-to-sunorcal-discovered/
- ESET InvisiMole June 2020: https://www.welivesecurity.com/wp-content/uploads/2020/06/ESET_InvisiMole.pdf
