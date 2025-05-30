---
alias: T1101
---

## T1101

Windows Security Support Provider (SSP) DLLs are loaded into the Local Security Authority (LSA) process at system start. Once loaded into the LSA, SSP DLLs have access to encrypted and plaintext passwords that are stored in Windows, such as any logged-on user's Domain password or smart card PINs. The SSP configuration is stored in two Registry keys: <code>HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Security Packages</code> and <code>HKLM\SYSTEM\CurrentControlSet\Control\Lsa\OSConfig\Security Packages</code>. An adversary may modify these Registry keys to add new SSPs, which will be loaded the next time the system boots, or when the AddSecurityPackage Windows API function is called.
 (Citation: Graeber 2014)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows

### Permissions Required
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Process Integrity\|M1025]] | Privileged Process Integrity | Windows 8.1, Windows Server 2012 R2, and later versions may make LSA run as a Protected Process Light (PPL) by setting the Registry key <code>HKLM\\SYSTEM\\CurrentControlSet\\Control\\Lsa\\RunAsPPL</code>, which requires all SSP DLLs to be signed by Microsoft. (Citation: Graeber 2014) (Citation: Microsoft Configure LSA) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1101
- Graeber 2014: http://docplayer.net/20839173-Analysis-of-malicious-security-support-provider-dlls.html
- Microsoft Configure LSA: https://technet.microsoft.com/en-us/library/dn408187.aspx
