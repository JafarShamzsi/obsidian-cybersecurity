---
alias: T1129
---

## T1129

Adversaries may execute malicious payloads via loading shared modules. Shared modules are executable files that are loaded into processes to provide access to reusable code, such as specific custom functions or invoking OS API functions (i.e., [Native API](https://attack.mitre.org/techniques/T1106)).

Adversaries may use this functionality as a way to execute arbitrary payloads on a victim system. For example, adversaries can modularize functionality of their malware into shared objects that perform various functions such as managing C2 network communications or execution of specific actions on objective.

The Linux & macOS module loader can load and execute shared objects from arbitrary local paths. This functionality resides in `dlfcn.h` in functions such as `dlopen` and `dlsym`. Although macOS can execute `.so` files, common practice uses `.dylib` files.(Citation: Apple Dev Dynamic Libraries)(Citation: Linux Shared Libraries)(Citation: RotaJakiro 2021 netlab360 analysis)(Citation: Unit42 OceanLotus 2017)

The Windows module loader can be instructed to load DLLs from arbitrary local paths and arbitrary Universal Naming Convention (UNC) network paths. This functionality resides in `NTDLL.dll` and is part of the Windows [Native API](https://attack.mitre.org/techniques/T1106) which is called from functions like `LoadLibrary` at run time.(Citation: Microsoft DLL)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Execution]] (TA0002)

### Platforms
- Windows
- macOS
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Identify and block potentially malicious software executed through this technique by using application control tools capable of preventing unknown modules from being loaded. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1129
- RotaJakiro 2021 netlab360 analysis: https://blog.netlab.360.com/stealth_rotajakiro_backdoor_en/
- Apple Dev Dynamic Libraries: https://developer.apple.com/library/archive/documentation/DeveloperTools/Conceptual/DynamicLibraries/100-Articles/OverviewOfDynamicLibraries.html
- Unit42 OceanLotus 2017: https://unit42.paloaltonetworks.com/unit42-new-improved-macos-backdoor-oceanlotus/
- Microsoft DLL: https://learn.microsoft.com/troubleshoot/windows-client/deployment/dynamic-link-library
- Linux Shared Libraries: https://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html
