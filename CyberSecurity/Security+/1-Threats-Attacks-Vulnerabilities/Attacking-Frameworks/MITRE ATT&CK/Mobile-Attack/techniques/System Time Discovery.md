---
alias: T1124
---

## T1124

An adversary may gather the system time and/or time zone settings from a local or remote system. The system time is set and stored by services, such as the Windows Time Service on Windows or <code>systemsetup</code> on macOS.(Citation: MSDN System Time)(Citation: Technet Windows Time Service)(Citation: systemsetup mac time) These time settings may also be synchronized between systems and services in an enterprise network, typically accomplished with a network time server within a domain.(Citation: Mac Time Sync)(Citation: linux system time)

System time information may be gathered in a number of ways, such as with [Net](https://attack.mitre.org/software/S0039) on Windows by performing <code>net time \\hostname</code> to gather the system time on a remote system. The victim's time zone may also be inferred from the current system time or gathered by using <code>w32tm /tz</code>.(Citation: Technet Windows Time Service) In addition, adversaries can discover device uptime through functions such as <code>GetTickCount()</code> to determine how long it has been since the system booted up.(Citation: Virtualization/Sandbox Evasion)

On network devices, [Network Device CLI](https://attack.mitre.org/techniques/T1059/008) commands such as `show clock detail` can be used to see the current time configuration.(Citation: show_clock_detail_cisco_cmd)

In addition, system calls – such as <code>time()</code> – have been used to collect the current time on Linux devices.(Citation: MAGNET GOBLIN) On macOS systems, adversaries may use commands such as <code>systemsetup -gettimezone</code> or <code>timeIntervalSinceNow</code> to gather current time zone information or current date and time.(Citation: System Information Discovery Technique)(Citation: ESET DazzleSpy Jan 2022)

This information could be useful for performing other techniques, such as executing a file with a [Scheduled Task/Job](https://attack.mitre.org/techniques/T1053)(Citation: RSA EU12 They're Inside), or to discover locality information based on time zone to assist in victim targeting (i.e. [System Location Discovery](https://attack.mitre.org/techniques/T1614)). Adversaries may also use knowledge of system time as part of a time bomb, or delaying execution until a specified date/time.(Citation: AnyRun TimeBomb)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows
- Network
- Linux
- macOS

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1124
- systemsetup mac time: https://support.apple.com/en-gb/guide/remote-desktop/apd95406b8d/mac
- linux system time: https://wiki.archlinux.org/title/System_time
- MAGNET GOBLIN: https://research.checkpoint.com/2024/magnet-goblin-targets-publicly-facing-servers-using-1-day-vulnerabilities/
- show_clock_detail_cisco_cmd: https://www.cisco.com/c/en/us/td/docs/ios-xml/ios/security/s1/sec-s1-cr-book/sec-cr-s2.html#wp1896741674
- Mac Time Sync: https://www.macinstruct.com/tutorials/synchronize-your-macs-clock-with-a-time-server/
- ESET DazzleSpy Jan 2022: https://www.welivesecurity.com/2022/01/25/watering-hole-deploys-new-macos-malware-dazzlespy-asia/
- AnyRun TimeBomb: https://any.run/cybersecurity-blog/time-bombs-malware-with-delayed-execution/
- Technet Windows Time Service: https://technet.microsoft.com/windows-server-docs/identity/ad-ds/get-started/windows-time-service/windows-time-service-tools-and-settings
- MSDN System Time: https://msdn.microsoft.com/ms724961.aspx
- RSA EU12 They're Inside: https://www.rsaconference.com/writable/presentations/file_upload/ht-209_rivner_schwartz.pdf
- System Information Discovery Technique: https://www.picussecurity.com/resource/the-system-information-discovery-technique-explained-mitre-attack-t1082
- Virtualization/Sandbox Evasion: https://www.picussecurity.com/resource/virtualization/sandbox-evasion-how-attackers-avoid-malware-analysis
