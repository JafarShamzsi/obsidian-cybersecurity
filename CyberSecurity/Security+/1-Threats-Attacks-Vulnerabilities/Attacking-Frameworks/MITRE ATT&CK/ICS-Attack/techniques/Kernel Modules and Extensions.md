---
alias: T1547.006
---

## T1547.006

Adversaries may modify the kernel to automatically execute programs on system boot. Loadable Kernel Modules (LKMs) are pieces of code that can be loaded and unloaded into the kernel upon demand. They extend the functionality of the kernel without the need to reboot the system. For example, one type of module is the device driver, which allows the kernel to access hardware connected to the system.(Citation: Linux Kernel Programming) 

When used maliciously, LKMs can be a type of kernel-mode [Rootkit](https://attack.mitre.org/techniques/T1014) that run with the highest operating system privilege (Ring 0).(Citation: Linux Kernel Module Programming Guide) Common features of LKM based rootkits include: hiding itself, selective hiding of files, processes and network activity, as well as log tampering, providing authenticated backdoors, and enabling root access to non-privileged users.(Citation: iDefense Rootkit Overview)

Kernel extensions, also called kext, are used in macOS to load functionality onto a system similar to LKMs for Linux. Since the kernel is responsible for enforcing security and the kernel extensions run as apart of the kernel, kexts are not governed by macOS security policies. Kexts are loaded and unloaded through <code>kextload</code> and <code>kextunload</code> commands. Kexts need to be signed with a developer ID that is granted privileges by Apple allowing it to sign Kernel extensions. Developers without these privileges may still sign kexts but they will not load unless SIP is disabled. If SIP is enabled, the kext signature is verified before being added to the AuxKC.(Citation: System and kernel extensions in macOS)

Since macOS Catalina 10.15, kernel extensions have been deprecated in favor of System Extensions. However, kexts are still allowed as "Legacy System Extensions" since there is no System Extension for Kernel Programming Interfaces.(Citation: Apple Kernel Extension Deprecation)

Adversaries can use LKMs and kexts to conduct [Persistence](https://attack.mitre.org/tactics/TA0003) and/or [Privilege Escalation](https://attack.mitre.org/tactics/TA0004) on a system. Examples have been found in the wild, and there are some relevant open source projects as well.(Citation: Volatility Phalanx2)(Citation: CrowdStrike Linux Rootkit)(Citation: GitHub Reptile)(Citation: GitHub Diamorphine)(Citation: RSAC 2015 San Francisco Patrick Wardle)(Citation: Synack Secure Kernel Extension Broken)(Citation: Securelist Ventir)(Citation: Trend Micro Skidmap)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- macOS
- Linux

### Permissions Required
- root

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Application control and software restriction tools, such as SELinux, KSPP, grsecurity MODHARDEN, and Linux kernel tuning can aid in restricting kernel module loading.(Citation: Kernel.org Restrict Kernel Module)(Citation: Wikibooks Grsecurity)(Citation: Kernel Self Protection Project)(Citation: Increasing Linux kernel integrity)(Citation: LKM loading kernel restrictions) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Use MDM to disable user's ability to install or approve kernel extensions, and ensure all approved kernel extensions are in alignment with policies specified in <code>com.apple.syspolicy.kernel-extension-policy</code>.(Citation: Apple TN2459 Kernel Extensions)(Citation: MDMProfileConfigMacOS)<br /> |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Limit access to the root account and prevent users from loading kernel modules and extensions through proper privilege separation and limiting Privilege Escalation opportunities. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Antivirus／Antimalware\|M1049]] | Antivirus／Antimalware | Common tools for detecting Linux rootkits include: rkhunter (Citation: SourceForge rkhunter), chrootkit (Citation: Chkrootkit Main), although rootkits may be designed to evade certain detection tools. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1547/006
- Apple Developer Configuration Profile: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf
- Apple Kernel Extension Deprecation: https://developer.apple.com/support/kernel-extensions/
- System and kernel extensions in macOS: https://support.apple.com/guide/deployment/system-and-kernel-extensions-in-macos-depa5fb8376f/web
- GitHub Reptile: https://github.com/f0rb1dd3n/Reptile
- Volatility Phalanx2: https://volatility-labs.blogspot.com/2012/10/phalanx-2-revealed-using-volatility-to.html
- iDefense Rootkit Overview: http://www.megasecurity.org/papers/Rootkits.pdf
- Linux Loadable Kernel Module Insert and Remove LKMs: http://tldp.org/HOWTO/Module-HOWTO/x197.html
- CrowdStrike Linux Rootkit: https://www.crowdstrike.com/blog/http-iframe-injecting-linux-rootkit/
- GitHub Diamorphine: https://github.com/m0nad/Diamorphine
- Securelist Ventir: https://securelist.com/the-ventir-trojan-assemble-your-macos-spy/67267/
- User Approved Kernel Extension Pike’s: https://pikeralpha.wordpress.com/2017/08/29/user-approved-kernel-extension-loading/
- Linux Kernel Module Programming Guide: http://www.tldp.org/LDP/lkmpg/2.4/html/x437.html
- Linux Kernel Programming: https://www.tldp.org/LDP/lkmpg/2.4/lkmpg.pdf
- Trend Micro Skidmap: https://blog.trendmicro.com/trendlabs-security-intelligence/skidmap-linux-malware-uses-rootkit-capabilities-to-hide-cryptocurrency-mining-payload/
- Purves Kextpocalypse 2: https://richard-purves.com/2017/11/09/mdm-and-the-kextpocalypse-2/
- RSAC 2015 San Francisco Patrick Wardle: https://www.virusbulletin.com/uploads/pdf/conference/vb2014/VB2014-Wardle.pdf
- Synack Secure Kernel Extension Broken: https://www.synack.com/2017/09/08/high-sierras-secure-kernel-extension-loading-is-broken/
- Wikipedia Loadable Kernel Module: https://en.wikipedia.org/wiki/Loadable_kernel_module#Linux
