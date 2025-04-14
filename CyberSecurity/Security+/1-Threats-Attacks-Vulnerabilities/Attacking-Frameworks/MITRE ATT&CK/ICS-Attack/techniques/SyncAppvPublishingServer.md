---
alias: T1216.002
---

## T1216.002

Adversaries may abuse SyncAppvPublishingServer.vbs to proxy execution of malicious [PowerShell](https://attack.mitre.org/techniques/T1059/001) commands. SyncAppvPublishingServer.vbs is a Visual Basic script associated with how Windows virtualizes applications (Microsoft Application Virtualization, or App-V).(Citation: 1 - appv) For example, Windows may render Win32 applications to users as virtual applications, allowing users to launch and interact with them as if they were installed locally.(Citation: 2 - appv)(Citation: 3 - appv)
    
The SyncAppvPublishingServer.vbs script is legitimate, may be signed by Microsoft, and is commonly executed from `\System32` through the command line via `wscript.exe`.(Citation: 4 - appv)(Citation: 5 - appv)

Adversaries may abuse SyncAppvPublishingServer.vbs to bypass [PowerShell](https://attack.mitre.org/techniques/T1059/001) execution restrictions and evade defensive counter measures by "living off the land."(Citation: 6 - appv)(Citation: 4 - appv) Proxying execution may function as a trusted/signed alternative to directly invoking `powershell.exe`.(Citation: 7 - appv)

For example,  [PowerShell](https://attack.mitre.org/techniques/T1059/001) commands may be invoked using:(Citation: 5 - appv)

`SyncAppvPublishingServer.vbs "n; {PowerShell}"`


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Certain signed scripts that can be used to execute other programs may not be necessary within a given environment. Use application control configured to block execution of these scripts if they are not required for a given system or network to prevent potential misuse by adversaries. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1216/002
- 4 - appv: https://www.trellix.com/en-ca/about/newsroom/stories/research/suspected-darkhotel-apt-activity-update/
- 2 - appv: https://learn.microsoft.com/en-us/windows/application-management/app-v/appv-getting-started
- 5 - appv: https://lolbas-project.github.io/lolbas/Scripts/Syncappvpublishingserver/
- 7 - appv: https://twitter.com/monoxgas/status/895045566090010624
- 3 - appv: https://www.hackingarticles.in/indirect-command-execution-defense-evasion-t1202/
- 1 - appv: https://securelist.com/bluenoroff-methods-bypass-motw/108383/
- 6 - appv: https://strontic.github.io/xcyclopedia/library/SyncAppvPublishingServer.exe-3C291419F60CDF9C2E4E19AD89944FA3.html
