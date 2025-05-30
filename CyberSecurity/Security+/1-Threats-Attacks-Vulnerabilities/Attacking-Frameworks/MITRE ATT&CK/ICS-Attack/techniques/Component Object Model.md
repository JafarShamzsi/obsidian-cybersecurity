---
alias: T1559.001
---

## T1559.001

Adversaries may use the Windows Component Object Model (COM) for local code execution. COM is an inter-process communication (IPC) component of the native Windows application programming interface (API) that enables interaction between software objects, or executable code that implements one or more interfaces.(Citation: Fireeye Hunting COM June 2019) Through COM, a client object can call methods of server objects, which are typically binary Dynamic Link Libraries (DLL) or executables (EXE).(Citation: Microsoft COM) Remote COM execution is facilitated by [Remote Services](https://attack.mitre.org/techniques/T1021) such as  [Distributed Component Object Model](https://attack.mitre.org/techniques/T1021/003) (DCOM).(Citation: Fireeye Hunting COM June 2019)

Various COM interfaces are exposed that can be abused to invoke arbitrary execution via a variety of programming languages such as C, C++, Java, and [Visual Basic](https://attack.mitre.org/techniques/T1059/005).(Citation: Microsoft COM) Specific COM objects also exist to directly perform functions beyond code execution, such as creating a [Scheduled Task/Job](https://attack.mitre.org/techniques/T1053), fileless download/execution, and other adversary behaviors related to privilege escalation and persistence.(Citation: Fireeye Hunting COM June 2019)(Citation: ProjectZero File Write EoP Apr 2018)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Execution]] (TA0002)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Modify Registry settings (directly or using Dcomcnfg.exe) in `HKEY_LOCAL_MACHINE\\SOFTWARE\\Classes\\AppID\\{AppID_GUID}` associated with the process-wide security of individual COM applications.(Citation: Microsoft Process Wide Com Keys)<br /><br />Modify Registry settings (directly or using Dcomcnfg.exe) in `HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Ole` associated with system-wide security defaults for all COM applications that do no set their own process-wide security.(Citation: Microsoft System Wide Com Keys) (Citation: Microsoft COM ACL) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Application Isolation and Sandboxing\|M1048]] | Application Isolation and Sandboxing | Ensure all COM alerts and Protected View are enabled.(Citation: Microsoft Protected View) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1559/001
- Fireeye Hunting COM June 2019: https://www.fireeye.com/blog/threat-research/2019/06/hunting-com-objects.html
- Microsoft COM: https://msdn.microsoft.com/library/windows/desktop/ms680573.aspx
- ProjectZero File Write EoP Apr 2018: https://googleprojectzero.blogspot.com/2018/04/windows-exploitation-tricks-exploiting.html
- Enigma Outlook DCOM Lateral Movement Nov 2017: https://enigma0x3.net/2017/11/16/lateral-movement-using-outlooks-createobject-method-and-dotnettojscript/
- Enigma MMC20 COM Jan 2017: https://enigma0x3.net/2017/01/05/lateral-movement-using-the-mmc20-application-com-object/
