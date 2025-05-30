---
alias: T1505.004
---

## T1505.004

Adversaries may install malicious components that run on Internet Information Services (IIS) web servers to establish persistence. IIS provides several mechanisms to extend the functionality of the web servers. For example, Internet Server Application Programming Interface (ISAPI) extensions and filters can be installed to examine and/or modify incoming and outgoing IIS web requests. Extensions and filters are deployed as DLL files that export three functions: <code>Get{Extension/Filter}Version</code>, <code>Http{Extension/Filter}Proc</code>, and (optionally) <code>Terminate{Extension/Filter}</code>. IIS modules may also be installed to extend IIS web servers.(Citation: Microsoft ISAPI Extension Overview 2017)(Citation: Microsoft ISAPI Filter Overview 2017)(Citation: IIS Backdoor 2011)(Citation: Trustwave IIS Module 2013)

Adversaries may install malicious ISAPI extensions and filters to observe and/or modify traffic, execute commands on compromised machines, or proxy command and control traffic. ISAPI extensions and filters may have access to all IIS web requests and responses. For example, an adversary may abuse these mechanisms to modify HTTP responses in order to distribute malicious commands/content to previously comprised hosts.(Citation: Microsoft ISAPI Filter Overview 2017)(Citation: Microsoft ISAPI Extension Overview 2017)(Citation: Microsoft ISAPI Extension All Incoming 2017)(Citation: Dell TG-3390)(Citation: Trustwave IIS Module 2013)(Citation: MMPC ISAPI Filter 2012)

Adversaries may also install malicious IIS modules to observe and/or modify traffic. IIS 7.0 introduced modules that provide the same unrestricted access to HTTP requests and responses as ISAPI extensions and filters. IIS modules can be written as a DLL that exports <code>RegisterModule</code>, or as a .NET application that interfaces with ASP.NET APIs to access IIS HTTP requests.(Citation: Microsoft IIS Modules Overview 2007)(Citation: Trustwave IIS Module 2013)(Citation: ESET IIS Malware 2021)


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
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Restrict unallowed ISAPI extensions and filters from running by specifying a list of ISAPI extensions and filters that can run on IIS.(Citation: Microsoft ISAPICGIRestriction 2016) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Code Signing\|M1045]] | Code Signing | Ensure IIS DLLs and binaries are signed by the correct application developers. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Do not allow administrator accounts that have permissions to add IIS components to be used for day-to-day operations that may expose these permissions to potential adversaries and/or other unprivileged systems. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Regularly check installed IIS components to verify the integrity of the web server and identify if unexpected changes have been made. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1505/004
- Microsoft ISAPI Extension Overview 2017: https://docs.microsoft.com/en-us/previous-versions/iis/6.0-sdk/ms525172(v=vs.90)
- Microsoft ISAPI Filter Overview 2017: https://docs.microsoft.com/en-us/previous-versions/iis/6.0-sdk/ms524610(v=vs.90)
- IIS Backdoor 2011: https://web.archive.org/web/20170106175935/http:/esec-lab.sogeti.com/posts/2011/02/02/iis-backdoor.html
- Trustwave IIS Module 2013: https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/the-curious-case-of-the-malicious-iis-module/
- Microsoft ISAPI Extension All Incoming 2017: https://docs.microsoft.com/en-us/previous-versions/iis/6.0-sdk/ms525696(v=vs.90)
- Dell TG-3390: https://www.secureworks.com/research/threat-group-3390-targets-organizations-for-cyberespionage
- MMPC ISAPI Filter 2012: https://web.archive.org/web/20140804175025/http:/blogs.technet.com/b/mmpc/archive/2012/10/03/malware-signed-with-the-adobe-code-signing-certificate.aspx
- Microsoft IIS Modules Overview 2007: https://docs.microsoft.com/en-us/iis/get-started/introduction-to-iis/iis-modules-overview
- ESET IIS Malware 2021: https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Anatomy-Of-Native-Iis-Malware-wp.pdf
- Unit 42 RGDoor Jan 2018: https://researchcenter.paloaltonetworks.com/2018/01/unit42-oilrig-uses-rgdoor-iis-backdoor-targets-middle-east/
