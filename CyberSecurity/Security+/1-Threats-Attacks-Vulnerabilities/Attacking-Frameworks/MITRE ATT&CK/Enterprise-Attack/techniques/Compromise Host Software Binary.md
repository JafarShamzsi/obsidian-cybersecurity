---
alias: T1554
---

## T1554

Adversaries may modify host software binaries to establish persistent access to systems. Software binaries/executables provide a wide range of system commands or services, programs, and libraries. Common software binaries are SSH clients, FTP clients, email clients, web browsers, and many other user or server applications.

Adversaries may establish persistence though modifications to host software binaries. For example, an adversary may replace or otherwise infect a legitimate application binary (or support files) with a backdoor. Since these binaries may be routinely executed by applications or the user, the adversary can leverage this for persistent access to the host.

An adversary may also modify an existing binary by patching in malicious functionality (e.g., IAT Hooking/Entry point patching)(Citation: Unit42 Banking Trojans Hooking 2022) prior to the binary’s legitimate execution. For example, an adversary may modify the entry point of a binary to point to malicious code patched in by the adversary before resuming normal execution flow.(Citation: ESET FontOnLake Analysis 2021)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Code Signing\|M1045]] | Code Signing | Ensure all application component binaries are signed by the correct application developers. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1554
- Unit42 Banking Trojans Hooking 2022: https://unit42.paloaltonetworks.com/banking-trojan-techniques/#post-125550-_rm3d6xxbk52n
- ESET FontOnLake Analysis 2021: https://web-assets.esetstatic.com/wls/2021/10/eset_fontonlake.pdf
