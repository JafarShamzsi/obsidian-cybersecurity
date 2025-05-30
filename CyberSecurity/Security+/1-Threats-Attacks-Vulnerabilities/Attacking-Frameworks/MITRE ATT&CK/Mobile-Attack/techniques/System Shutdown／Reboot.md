---
alias: T1529
---

## T1529

Adversaries may shutdown/reboot systems to interrupt access to, or aid in the destruction of, those systems. Operating systems may contain commands to initiate a shutdown/reboot of a machine or network device. In some cases, these commands may also be used to initiate a shutdown/reboot of a remote computer or network device via [Network Device CLI](https://attack.mitre.org/techniques/T1059/008) (e.g. <code>reload</code>).(Citation: Microsoft Shutdown Oct 2017)(Citation: alert_TA18_106A)

Shutting down or rebooting systems may disrupt access to computer resources for legitimate users while also impeding incident response/recovery.

Adversaries may attempt to shutdown/reboot a system after impacting it in other ways, such as [Disk Structure Wipe](https://attack.mitre.org/techniques/T1561/002) or [Inhibit System Recovery](https://attack.mitre.org/techniques/T1490), to hasten the intended effects on system availability.(Citation: Talos Nyetya June 2017)(Citation: Talos Olympic Destroyer 2018)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Impact]] (TA0040)

### Platforms
- Linux
- macOS
- Windows
- Network

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1529
- Talos Nyetya June 2017: https://blog.talosintelligence.com/2017/06/worldwide-ransomware-variant.html
- alert_TA18_106A: https://www.cisa.gov/uscert/ncas/alerts/TA18-106A
- Talos Olympic Destroyer 2018: https://blog.talosintelligence.com/2018/02/olympic-destroyer.html
- Microsoft Shutdown Oct 2017: https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/shutdown
