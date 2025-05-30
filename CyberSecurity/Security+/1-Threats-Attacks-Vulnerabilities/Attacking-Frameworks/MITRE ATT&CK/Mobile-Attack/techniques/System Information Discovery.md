---
alias: T1082
---

## T1082

An adversary may attempt to get detailed information about the operating system and hardware, including version, patches, hotfixes, service packs, and architecture. Adversaries may use the information from [System Information Discovery](https://attack.mitre.org/techniques/T1082) during automated discovery to shape follow-on behaviors, including whether or not the adversary fully infects the target and/or attempts specific actions.

Tools such as [Systeminfo](https://attack.mitre.org/software/S0096) can be used to gather detailed system information. If running with privileged access, a breakdown of system data can be gathered through the <code>systemsetup</code> configuration tool on macOS. As an example, adversaries with user-level access can execute the <code>df -aH</code> command to obtain currently mounted disks and associated freely available space. Adversaries may also leverage a [Network Device CLI](https://attack.mitre.org/techniques/T1059/008) on network devices to gather detailed system information (e.g. <code>show version</code>).(Citation: US-CERT-TA18-106A) [System Information Discovery](https://attack.mitre.org/techniques/T1082) combined with information gathered from other forms of discovery and reconnaissance can drive payload development and concealment.(Citation: OSX.FairyTale)(Citation: 20 macOS Common Tools and Techniques)

Infrastructure as a Service (IaaS) cloud providers such as AWS, GCP, and Azure allow access to instance and virtual machine information via APIs. Successful authenticated API calls can return data such as the operating system platform and status of a particular instance or the model view of a virtual machine.(Citation: Amazon Describe Instance)(Citation: Google Instances Resource)(Citation: Microsoft Virutal Machine API)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Windows
- IaaS
- Linux
- macOS
- Network

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1082
- Amazon Describe Instance: https://docs.aws.amazon.com/cli/latest/reference/ssm/describe-instance-information.html
- Google Instances Resource: https://cloud.google.com/compute/docs/reference/rest/v1/instances
- Microsoft Virutal Machine API: https://docs.microsoft.com/en-us/rest/api/compute/virtualmachines/get
- 20 macOS Common Tools and Techniques: https://labs.sentinelone.com/20-common-tools-techniques-used-by-macos-threat-actors-malware/
- OSX.FairyTale: https://www.sentinelone.com/blog/trail-osx-fairytale-adware-playing-malware/
- US-CERT-TA18-106A: https://www.us-cert.gov/ncas/alerts/TA18-106A
