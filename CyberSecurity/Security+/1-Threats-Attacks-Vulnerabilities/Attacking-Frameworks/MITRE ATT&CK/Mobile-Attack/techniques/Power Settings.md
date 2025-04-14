---
alias: T1653
---

## T1653

Adversaries may impair a system's ability to hibernate, reboot, or shut down in order to extend access to infected machines. When a computer enters a dormant state, some or all software and hardware may cease to operate which can disrupt malicious activity.(Citation: Sleep, shut down, hibernate)

Adversaries may abuse system utilities and configuration settings to maintain access by preventing machines from entering a state, such as standby, that can terminate malicious activity.(Citation: Microsoft: Powercfg command-line options)(Citation: systemdsleep Linux)

For example, `powercfg` controls all configurable power system settings on a Windows system and can be abused to prevent an infected host from locking or shutting down.(Citation: Two New Monero Malware Attacks Target Windows and Android Users) Adversaries may also extend system lock screen timeout settings.(Citation: BATLOADER: The Evasive Downloader Malware) Other relevant settings, such as disk and hibernate timeout, can be similarly abused to keep the infected machine running even if no user is active.(Citation: CoinLoader: A Sophisticated Malware Loader Campaign)

Aware that some malware cannot survive system reboots, adversaries may entirely delete files used to invoke system shut down or reboot.(Citation: Condi-Botnet-binaries)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows
- Linux
- macOS
- Network

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Periodically inspect systems for abnormal and unexpected power settings that may indicate malicious activty. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1653
- Sleep, shut down, hibernate: https://www.avg.com/en/signal/should-you-shut-down-sleep-or-hibernate-your-pc-or-mac-laptop
- CoinLoader: A Sophisticated Malware Loader Campaign: https://www.avira.com/en/blog/coinloader-a-sophisticated-malware-loader-campaign
- BATLOADER: The Evasive Downloader Malware: https://blogs.vmware.com/security/2022/11/batloader-the-evasive-downloader-malware.html
- Two New Monero Malware Attacks Target Windows and Android Users: https://securityintelligence.com/news/two-new-monero-malware-attacks-target-windows-and-android-users/
- Condi-Botnet-binaries: https://www.fortinet.com/blog/threat-research/condi-ddos-botnet-spreads-via-tp-links-cve-2023-1389
- systemdsleep Linux: https://man7.org/linux/man-pages/man5/systemd-sleep.conf.5.html
- Microsoft: Powercfg command-line options: https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/powercfg-command-line-options?adlt=strict
