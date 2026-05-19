---
alias: T1562.006
---

## T1562.006

An adversary may attempt to block indicators or events typically captured by sensors from being gathered and analyzed. This could include maliciously redirecting(Citation: Microsoft Lamin Sept 2017) or even disabling host-based sensors, such as Event Tracing for Windows (ETW)(Citation: Microsoft About Event Tracing 2018), by tampering settings that control the collection and flow of event telemetry.(Citation: Medium Event Tracing Tampering 2018) These settings may be stored on the system in configuration files and/or in the Registry as well as being accessible via administrative utilities such as [PowerShell](https://attack.mitre.org/techniques/T1059/001) or [Windows Management Instrumentation](https://attack.mitre.org/techniques/T1047).

For example, adversaries may modify the `File` value in <code>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog\Security</code> to hide their malicious actions in a new or different .evtx log file. This action does not require a system reboot and takes effect immediately.(Citation: disable_win_evt_logging) 

ETW interruption can be achieved multiple ways, however most directly by defining conditions using the [PowerShell](https://attack.mitre.org/techniques/T1059/001) <code>Set-EtwTraceProvider</code> cmdlet or by interfacing directly with the Registry to make alterations.

In the case of network-based reporting of indicators, an adversary may block traffic associated with reporting to prevent central analysis. This may be accomplished by many means, such as stopping a local process responsible for forwarding telemetry and/or creating a host-based firewall rule to block traffic to specific hosts responsible for aggregating events, such as security information and event management (SIEM) products.

In Linux environments, adversaries may disable or reconfigure log processing tools such as syslog or nxlog to inhibit detection and monitoring capabilities to facilitate follow on behaviors (Citation: LemonDuck).


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows
- macOS
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Ensure event tracers/forwarders (Citation: Microsoft ETW May 2018), firewall policies, and other associated mechanisms are secured with appropriate permissions and access controls and cannot be manipulated by user accounts. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Ensure event tracers/forwarders (Citation: Microsoft ETW May 2018), firewall policies, and other associated mechanisms are secured with appropriate permissions and access controls. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Consider automatically relaunching forwarding mechanisms at recurring intervals (ex: temporal, on-logon, etc.) as well as applying appropriate change management to firewall rules and other related system configurations. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1562/006
- disable_win_evt_logging: https://ptylu.github.io/content/report/report.html?report=25
- LemonDuck: https://www.crowdstrike.com/blog/lemonduck-botnet-targets-docker-for-cryptomining-operations/
- Microsoft Lamin Sept 2017: https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?name=Backdoor:Win32/Lamin.A
- Microsoft About Event Tracing 2018: https://docs.microsoft.com/en-us/windows/desktop/etw/consuming-events
- Medium Event Tracing Tampering 2018: https://medium.com/palantir/tampering-with-windows-event-tracing-background-offense-and-defense-4be7ac62ac63
