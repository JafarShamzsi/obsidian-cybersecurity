---
alias: T1552.006
---

## T1552.006

Adversaries may attempt to find unsecured credentials in Group Policy Preferences (GPP). GPP are tools that allow administrators to create domain policies with embedded credentials. These policies allow administrators to set local accounts.(Citation: Microsoft GPP 2016)

These group policies are stored in SYSVOL on a domain controller. This means that any domain user can view the SYSVOL share and decrypt the password (using the AES key that has been made public).(Citation: Microsoft GPP Key)

The following tools and scripts can be used to gather and decrypt the password file from Group Policy Preference XML files:

* Metasploit’s post exploitation module: <code>post/windows/gather/credentials/gpp</code>
* Get-GPPPassword(Citation: Obscuresecurity Get-GPPPassword)
* gpprefdecrypt.py

On the SYSVOL share, adversaries may use the following command to enumerate potential GPP XML files: <code>dir /s * .xml</code>



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Search SYSVOL for any existing GGPs that may contain credentials and remove them.(Citation: ADSecurity Finding Passwords in SYSVOL) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Active Directory Configuration\|M1015]] | Active Directory Configuration | Remove vulnerable Group Policy Preferences.(Citation: Microsoft MS14-025) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Update Software\|M1051]] | Update Software | Apply patch KB2962486 which prevents credentials from being stored in GPPs.(Citation: ADSecurity Finding Passwords in SYSVOL)(Citation: MS14-025) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1552/006
- Microsoft GPP 2016: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn581922(v%3Dws.11)
- Microsoft GPP Key: https://msdn.microsoft.com/library/cc422924.aspx
- Obscuresecurity Get-GPPPassword: https://obscuresecurity.blogspot.co.uk/2012/05/gpp-password-retrieval-with-powershell.html
- ADSecurity Finding Passwords in SYSVOL: https://adsecurity.org/?p=2288
