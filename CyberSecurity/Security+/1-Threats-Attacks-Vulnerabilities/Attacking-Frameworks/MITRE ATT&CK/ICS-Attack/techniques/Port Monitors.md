---
alias: T1547.010
---

## T1547.010

Adversaries may use port monitors to run an adversary supplied DLL during system boot for persistence or privilege escalation. A port monitor can be set through the <code>AddMonitor</code> API call to set a DLL to be loaded at startup.(Citation: AddMonitor) This DLL can be located in <code>C:\Windows\System32</code> and will be loaded and run by the print spooler service, `spoolsv.exe`, under SYSTEM level permissions on boot.(Citation: Bloxham) 

Alternatively, an arbitrary DLL can be loaded if permissions allow writing a fully-qualified pathname for that DLL to the `Driver` value of an existing or new arbitrarily named subkey of <code>HKLM\SYSTEM\CurrentControlSet\Control\Print\Monitors</code>. The Registry key contains entries for the following:

* Local Port
* Standard TCP/IP Port
* USB Monitor
* WSD Port



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Windows

### Permissions Required
- SYSTEM
- Administrator

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1547/010
- Bloxham: https://www.defcon.org/images/defcon-22/dc-22-presentations/Bloxham/DEFCON-22-Brady-Bloxham-Windows-API-Abuse-UPDATED.pdf
- AddMonitor: http://msdn.microsoft.com/en-us/library/dd183341
- TechNet Autoruns: https://technet.microsoft.com/en-us/sysinternals/bb963902
