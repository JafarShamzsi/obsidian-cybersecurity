---
alias: T1209
---

## T1209

The Windows Time service (W32Time) enables time synchronization across and within domains. (Citation: Microsoft W32Time Feb 2018) W32Time time providers are responsible for retrieving time stamps from hardware/network resources and outputting these values to other network clients. (Citation: Microsoft TimeProvider)

Time providers are implemented as dynamic-link libraries (DLLs) that are registered in the subkeys of  <code>HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\W32Time\TimeProviders\</code>. (Citation: Microsoft TimeProvider) The time provider manager, directed by the service control manager, loads and starts time providers listed and enabled under this key at system startup and/or whenever parameters are changed. (Citation: Microsoft TimeProvider)

Adversaries may abuse this architecture to establish Persistence, specifically by registering and enabling a malicious DLL as a time provider. Administrator privileges are required for time provider registration, though execution will run in context of the Local Service account. (Citation: Github W32Time Oct 2017)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows

### Permissions Required
- Administrator
- SYSTEM

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Consider using Group Policy to configure and block additions/modifications to W32Time DLLs. (Citation: Microsoft W32Time May 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Restrict Registry Permissions\|M1024]] | Restrict Registry Permissions | Consider using Group Policy to configure and block modifications to W32Time parameters in the Registry. (Citation: Microsoft W32Time May 2017) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1209
- Microsoft W32Time Feb 2018: https://docs.microsoft.com/windows-server/networking/windows-time-service/windows-time-service-top
- Microsoft TimeProvider: https://msdn.microsoft.com/library/windows/desktop/ms725475.aspx
- Github W32Time Oct 2017: https://github.com/scottlundgren/w32time
- Microsoft W32Time May 2017: https://docs.microsoft.com/windows-server/networking/windows-time-service/windows-time-service-tools-and-settings
- TechNet Autoruns: https://technet.microsoft.com/en-us/sysinternals/bb963902
