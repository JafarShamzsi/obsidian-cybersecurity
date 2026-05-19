---
alias: T1574.007
---

## T1574.007

Adversaries may execute their own malicious payloads by hijacking environment variables used to load libraries. The PATH environment variable contains a list of directories (User and System) that the OS searches sequentially through in search of the binary that was called from a script or the command line. 

Adversaries can place a malicious program in an earlier entry in the list of directories stored in the PATH environment variable, resulting in the operating system executing the malicious binary rather than the legitimate binary when it searches sequentially through that PATH listing.

For example, on Windows if an adversary places a malicious program named "net.exe" in `C:\example path`, which by default precedes `C:\Windows\system32\net.exe` in the PATH environment variable, when "net" is executed from the command-line the `C:\example path` will be called instead of the system's legitimate executable at `C:\Windows\system32\net.exe`. Some methods of executing a program rely on the PATH environment variable to determine the locations that are searched when the path for the program is not given, such as executing programs from a [Command and Scripting Interpreter](https://attack.mitre.org/techniques/T1059).(Citation: ExpressVPN PATH env Windows 2021)

Adversaries may also directly modify the $PATH variable specifying the directories to be searched.  An adversary can modify the `$PATH` variable to point to a directory they have write access. When a program using the $PATH variable is called, the OS searches the specified directory and executes the malicious binary. On macOS, this can also be performed through modifying the $HOME variable. These variables can be modified using the command-line, launchctl, [Unix Shell Configuration Modification](https://attack.mitre.org/techniques/T1546/004), or modifying the `/etc/paths.d` folder contents.(Citation: uptycs Fake POC linux malware 2023)(Citation: nixCraft macOS PATH variables)(Citation: Elastic Rules macOS launchctl 2022)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows
- macOS
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Adversaries will likely need to place new binaries in locations to be executed through this weakness. Identify and block potentially malicious software executed path interception by using application control tools, like Windows Defender Application Control, AppLocker, or Software Restriction Policies where appropriate.(Citation: SANS Application Whitelisting)(Citation: Microsoft Windows Defender Application Control)(Citation: Windows Commands JPCERT)(Citation: NSA MS AppLocker)(Citation: Microsoft Application Lockdown)(Citation: Microsoft Using Software Restriction ) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Ensure that proper permissions and directory access control are set to deny users the ability to write files to the top-level directory <code>C:</code> and system directories, such as <code>C:\Windows\</code>, to reduce places where malicious files could be placed for execution. Require that all executables be placed in write-protected directories. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Find and eliminate path interception weaknesses in program configuration files, scripts, the PATH environment variable, services, and in shortcuts by surrounding PATH variables with quotation marks when functions allow for them. Be aware of the search order Windows uses for executing or loading binaries and use fully qualified paths wherever appropriate.<br /><br />Clean up old Windows Registry keys when software is uninstalled to avoid keys with no associated legitimate binaries. Periodically search for and correct or report path interception weaknesses on systems that may have been introduced using custom or available tools that report software using insecure path configurations.(Citation: Microsoft CreateProcess)(Citation: Microsoft Dynamic-Link Library Security)(Citation: Vulnerability and Exploit Detector) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1574/007
- Elastic Rules macOS launchctl 2022: https://www.elastic.co/guide/en/security/7.17/prebuilt-rule-7-16-4-modification-of-environment-variable-via-launchctl.html
- ExpressVPN PATH env Windows 2021: https://www.expressvpn.com/blog/cybersecurity-lessons-a-path-vulnerability-in-windows/
- uptycs Fake POC linux malware 2023: https://www.uptycs.com/blog/new-poc-exploit-backdoor-malware
- nixCraft macOS PATH variables: https://www.cyberciti.biz/faq/appleosx-bash-unix-change-set-path-environment-variable/
