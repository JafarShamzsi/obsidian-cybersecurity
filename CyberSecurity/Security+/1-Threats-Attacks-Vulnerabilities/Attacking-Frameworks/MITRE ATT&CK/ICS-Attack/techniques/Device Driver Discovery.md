---
alias: T1652
---

## T1652

Adversaries may attempt to enumerate local device drivers on a victim host. Information about device drivers may highlight various insights that shape follow-on behaviors, such as the function/purpose of the host, present security tools (i.e. [Security Software Discovery](https://attack.mitre.org/techniques/T1518/001)) or other defenses (e.g., [Virtualization/Sandbox Evasion](https://attack.mitre.org/techniques/T1497)), as well as potential exploitable vulnerabilities (e.g., [Exploitation for Privilege Escalation](https://attack.mitre.org/techniques/T1068)).

Many OS utilities may provide information about local device drivers, such as `driverquery.exe` and the `EnumDeviceDrivers()` API function on Windows.(Citation: Microsoft Driverquery)(Citation: Microsoft EnumDeviceDrivers) Information about device drivers (as well as associated services, i.e., [System Service Discovery](https://attack.mitre.org/techniques/T1007)) may also be available in the Registry.(Citation: Microsoft Registry Drivers)

On Linux/macOS, device drivers (in the form of kernel modules) may be visible within `/dev` or using utilities such as `lsmod` and `modinfo`.(Citation: Linux Kernel Programming)(Citation: lsmod man)(Citation: modinfo man)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1652
- lsmod man: https://man7.org/linux/man-pages/man8/lsmod.8.html
- Microsoft Registry Drivers: https://learn.microsoft.com/windows-hardware/drivers/install/overview-of-registry-trees-and-keys
- Microsoft EnumDeviceDrivers: https://learn.microsoft.com/windows/win32/api/psapi/nf-psapi-enumdevicedrivers
- Microsoft Driverquery: https://learn.microsoft.com/windows-server/administration/windows-commands/driverquery
- Linux Kernel Programming: https://www.tldp.org/LDP/lkmpg/2.4/lkmpg.pdf
- modinfo man: https://linux.die.net/man/8/modinfo
