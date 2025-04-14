---
alias: 
---

## G0057




### Techniques Used

| ID | Name | Use |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Remote Desktop Protocol\|T1076]] | Remote Desktop Protocol | APT34 uses Remote Desktop Protocol for lateral movement. The group has also used tunneling tools to tunnel RDP into the environment. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Brute Force\|T1110]] | Brute Force | APT34 has used brute force techniques to obtain credentials. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Screen Capture\|T1113]] | Screen Capture | APT34 has a tool called CANDYKING to capture a screenshot of user's desktop. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Input Capture\|T1056]] | Input Capture | APT34 has used a keylogging tool called KEYPUNCH. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Web Shell\|T1100]] | Web Shell | APT34 has frequently used Web shells, often to maintain access to a victim network. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Obfuscated Files or Information\|T1027]] | Obfuscated Files or Information | APT34 has used base64-encoded files that are dropped to victims. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/OS Credential Dumping\|T1003]] | OS Credential Dumping | APT34 has dumped credentials from victims in several ways, including by using open source tools Mimikatz and Lazagne, or by harvesting credentials when users log into Outlook Web Access. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Network Service Discovery\|T1046]] | Network Service Discovery | APT34 has used the publicly available tool SoftPerfect Network Scanner as well as a custom tool called GOLDIRONY to conduct network scanning. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Application Layer Protocol\|T1071]] | Application Layer Protocol | APT34 malware often uses HTTP and DNS for C2. The group has also used the Plink utility and other tools to create tunnels to C2 servers. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Password Policy Discovery\|T1201]] | Password Policy Discovery | APT34 has used net.exe in a script with <code>net accounts /domain</code> to find the password policy of a domain. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Valid Accounts\|T1078]] | Valid Accounts | APT34 has used valid administrator credentials to assist in lateral movement. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/PowerShell\|T1086]] | PowerShell | APT34 has used PowerShell scripts for execution. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Command and Scripting Interpreter\|T1059]] | Command and Scripting Interpreter | APT34 has used the command-line interface for execution. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Standard Cryptographic Protocol\|T1032]] | Standard Cryptographic Protocol | APT34 used the Plink utility and other tools to create tunnels to C2 servers. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/File Deletion\|T1107]] | File Deletion | APT34 has deleted initial drop files from the staging directory. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/External Remote Services\|T1133]] | External Remote Services | APT34 uses remote services such as VPN, Citrix, or OWA to persist in an environment. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Windows Management Instrumentation\|T1047]] | Windows Management Instrumentation | APT34 has used WMI for execution. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Deobfuscate／Decode Files or Information\|T1140]] | Deobfuscate／Decode Files or Information | APT34 has used certutil to decode base64-encoded files on victims. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Ingress Tool Transfer\|T1105]] | Ingress Tool Transfer | APT34 can download remote files onto victims. |
