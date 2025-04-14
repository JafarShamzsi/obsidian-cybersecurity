---
alias: T1562.009
---

## T1562.009

Adversaries may abuse Windows safe mode to disable endpoint defenses. Safe mode starts up the Windows operating system with a limited set of drivers and services. Third-party security software such as endpoint detection and response (EDR) tools may not start after booting Windows in safe mode. There are two versions of safe mode: Safe Mode and Safe Mode with Networking. It is possible to start additional services after a safe mode boot.(Citation: Microsoft Safe Mode)(Citation: Sophos Snatch Ransomware 2019)

Adversaries may abuse safe mode to disable endpoint defenses that may not start with a limited boot. Hosts can be forced into safe mode after the next reboot via modifications to Boot Configuration Data (BCD) stores, which are files that manage boot application settings.(Citation: Microsoft bcdedit 2021)

Adversaries may also add their malicious applications to the list of minimal services that start in safe mode by modifying relevant Registry values (i.e. [Modify Registry](https://attack.mitre.org/techniques/T1112)). Malicious [Component Object Model](https://attack.mitre.org/techniques/T1559/001) (COM) objects may also be registered and loaded in safe mode.(Citation: Sophos Snatch Ransomware 2019)(Citation: CyberArk Labs Safe Mode 2016)(Citation: Cybereason Nocturnus MedusaLocker 2020)(Citation: BleepingComputer REvil 2021)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Restrict administrator accounts to as few individuals as possible, following least privilege principles, that may be abused to remotely boot a machine in safe mode.(Citation: CyberArk Labs Safe Mode 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Ensure that endpoint defenses run in safe mode.(Citation: CyberArk Labs Safe Mode 2016) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1562/009
- Microsoft Safe Mode: https://support.microsoft.com/en-us/windows/start-your-pc-in-safe-mode-in-windows-10-92c27cff-db89-8644-1ce4-b3e5e56fe234
- Sophos Snatch Ransomware 2019: https://news.sophos.com/en-us/2019/12/09/snatch-ransomware-reboots-pcs-into-safe-mode-to-bypass-protection/
- Microsoft bcdedit 2021: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/bcdedit
- CyberArk Labs Safe Mode 2016: https://www.cyberark.com/resources/blog/cyberark-labs-from-safe-mode-to-domain-compromise
- Cybereason Nocturnus MedusaLocker 2020: https://www.cybereason.com/blog/medusalocker-ransomware
- BleepingComputer REvil 2021: https://www.bleepingcomputer.com/news/security/revil-ransomware-has-a-new-windows-safe-mode-encryption-mode/
- Microsoft Bootcfg: https://docs.microsoft.com/windows-server/administration/windows-commands/bootcfg
