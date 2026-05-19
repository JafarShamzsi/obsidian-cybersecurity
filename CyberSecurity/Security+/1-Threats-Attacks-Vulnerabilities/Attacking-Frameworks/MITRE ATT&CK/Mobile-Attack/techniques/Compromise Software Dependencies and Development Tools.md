---
alias: T1195.001
---

## T1195.001

Adversaries may manipulate software dependencies and development tools prior to receipt by a final consumer for the purpose of data or system compromise. Applications often depend on external software to function properly. Popular open source projects that are used as dependencies in many applications may be targeted as a means to add malicious code to users of the dependency.(Citation: Trendmicro NPM Compromise)  

Targeting may be specific to a desired victim set or may be distributed to a broad set of consumers but only move on to additional tactics on specific victims. 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Initial Access]] (TA0001)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Vulnerability Scanning\|M1016]] | Vulnerability Scanning | Continuous monitoring of vulnerability sources and the use of automatic and manual code review tools should also be implemented as well.(Citation: OWASP Top 10) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Limit Software Installation\|M1033]] | Limit Software Installation | Where possible, consider requiring developers to pull from internal repositories containing verified and approved packages rather than from external ones.(Citation: Cider Security Top 10 CICD Security Risks) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Application Developer Guidance\|M1013]] | Application Developer Guidance | Application developers should be cautious when selecting third-party libraries to integrate into their application. Additionally, where possible, developers should lock software dependencies to specific versions rather than pulling the latest version on build.(Citation: Cider Security Top 10 CICD Security Risks) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Update Software\|M1051]] | Update Software | A patch management process should be implemented to check unused dependencies, unmaintained and/or previously vulnerable dependencies, unnecessary features, components, files, and documentation. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1195/001
- Trendmicro NPM Compromise: https://www.trendmicro.com/vinfo/dk/security/news/cybercrime-and-digital-threats/hacker-infects-node-js-package-to-steal-from-bitcoin-wallets
