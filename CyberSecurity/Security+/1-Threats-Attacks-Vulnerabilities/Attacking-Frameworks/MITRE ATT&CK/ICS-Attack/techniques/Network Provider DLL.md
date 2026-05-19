---
alias: T1556.008
---

## T1556.008

Adversaries may register malicious network provider dynamic link libraries (DLLs) to capture cleartext user credentials during the authentication process. Network provider DLLs allow Windows to interface with specific network protocols and can also support add-on credential management functions.(Citation: Network Provider API) During the logon process, Winlogon (the interactive logon module) sends credentials to the local `mpnotify.exe` process via RPC. The `mpnotify.exe` process then shares the credentials in cleartext with registered credential managers when notifying that a logon event is happening.(Citation: NPPSPY - Huntress)(Citation: NPPSPY Video)(Citation: NPLogonNotify) 

Adversaries can configure a malicious network provider DLL to receive credentials from `mpnotify.exe`.(Citation: NPPSPY) Once installed as a credential manager (via the Registry), a malicious DLL can receive and save credentials each time a user logs onto a Windows workstation or domain via the `NPLogonNotify()` function.(Citation: NPLogonNotify)

Adversaries may target planting malicious network provider DLLs on systems known to have increased logon activity and/or administrator logon activity, such as servers and domain controllers.(Citation: NPPSPY - Huntress)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Operating System Configuration\|M1028]] | Operating System Configuration | Starting in Windows 11 22H2, the `EnableMPRNotifications` policy can be disabled through Group Policy or through a configuration service provider to prevent Winlogon from sending credentials to network providers.(Citation: EnableMPRNotifications) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict Registry Permissions\|M1024]] | Restrict Registry Permissions | Restrict Registry permissions to disallow the modification of sensitive Registry keys such as `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\NetworkProvider\Order`. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Periodically review for new and unknown network provider DLLs within the Registry (`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\<NetworkProviderName>\NetworkProvider\ProviderPath`).<br /><br />Ensure only valid network provider DLLs are registered. The name of these can be found in the Registry key at `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\NetworkProvider\Order`, and have corresponding service subkey pointing to a DLL at `HKEY_LOCAL_MACHINE\SYSTEM\CurrentC ontrolSet\Services\<NetworkProviderName>\NetworkProvider`. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1556/008
- NPPSPY - Huntress: https://www.huntress.com/blog/cleartext-shenanigans-gifting-user-passwords-to-adversaries-with-nppspy
- NPPSPY Video: https://www.youtube.com/watch?v=ggY3srD9dYs
- NPPSPY: https://github.com/gtworek/PSBits/tree/master/PasswordStealing/NPPSpy
- Network Provider API: https://learn.microsoft.com/en-us/windows/win32/secauthn/network-provider-api
- NPLogonNotify: https://learn.microsoft.com/en-us/windows/win32/api/npapi/nf-npapi-nplogonnotify
