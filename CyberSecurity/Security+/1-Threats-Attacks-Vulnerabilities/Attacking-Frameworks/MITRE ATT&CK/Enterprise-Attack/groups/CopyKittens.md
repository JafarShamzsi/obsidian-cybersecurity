---
alias: CopyKittens
---

## G0052

[CopyKittens](https://attack.mitre.org/groups/G0052) is an Iranian cyber espionage group that has been operating since at least 2013. It has targeted countries including Israel, Saudi Arabia, Turkey, the U.S., Jordan, and Germany. The group is responsible for the campaign known as Operation Wilted Tulip.(Citation: ClearSky CopyKittens March 2017)(Citation: ClearSky Wilted Tulip July 2017)(Citation: CopyKittens Nov 2015)


### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Archive via Custom Method\|T1560.003]] | Archive via Custom Method | [CopyKittens](https://attack.mitre.org/groups/G0052) encrypts data with a substitute cipher prior to exfiltration.(Citation: CopyKittens Nov 2015) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Archive via Utility\|T1560.001]] | Archive via Utility | [CopyKittens](https://attack.mitre.org/groups/G0052) uses ZPP, a .NET console program, to compress files with ZIP.(Citation: ClearSky Wilted Tulip July 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/PowerShell\|T1059.001]] | PowerShell | [CopyKittens](https://attack.mitre.org/groups/G0052) has used PowerShell Empire.(Citation: ClearSky Wilted Tulip July 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Proxy\|T1090]] | Proxy | [CopyKittens](https://attack.mitre.org/groups/G0052) has used the AirVPN service for operational activity.(Citation: Microsoft POLONIUM June 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Rundll32\|T1218.011]] | Rundll32 | [CopyKittens](https://attack.mitre.org/groups/G0052) uses rundll32 to load various tools on victims, including a lateral movement tool named Vminst, Cobalt Strike, and shellcode.(Citation: ClearSky Wilted Tulip July 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Hidden Window\|T1564.003]] | Hidden Window | [CopyKittens](https://attack.mitre.org/groups/G0052) has used <code>-w hidden</code> and <code>-windowstyle hidden</code> to conceal [PowerShell](https://attack.mitre.org/techniques/T1059/001) windows. (Citation: ClearSky Wilted Tulip July 2017) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Tool\|T1588.002]] | Tool | [CopyKittens](https://attack.mitre.org/groups/G0052) has used Metasploit, [Empire](https://attack.mitre.org/software/S0363), and AirVPN for post-exploitation activities.(Citation: ClearSky and Trend Micro Operation Wilted Tulip July 2017)(Citation: Microsoft POLONIUM June 2022) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Enterprise-Attack/techniques/Code Signing\|T1553.002]] | Code Signing | [CopyKittens](https://attack.mitre.org/groups/G0052) digitally signed an executable with a stolen certificate from legitimate company AI Squared.(Citation: ClearSky Wilted Tulip July 2017) |
