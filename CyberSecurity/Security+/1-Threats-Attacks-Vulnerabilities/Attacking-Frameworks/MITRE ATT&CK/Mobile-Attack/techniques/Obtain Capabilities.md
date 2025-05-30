---
alias: T1588
---

## T1588

Adversaries may buy and/or steal capabilities that can be used during targeting. Rather than developing their own capabilities in-house, adversaries may purchase, freely download, or steal them. Activities may include the acquisition of malware, software (including licenses), exploits, certificates, and information relating to vulnerabilities. Adversaries may obtain capabilities to support their operations throughout numerous phases of the adversary lifecycle.

In addition to downloading free malware, software, and exploits from the internet, adversaries may purchase these capabilities from third-party entities. Third-party entities can include technology companies that specialize in malware and exploits, criminal marketplaces, or from individuals.(Citation: NationsBuying)(Citation: PegasusCitizenLab)

In addition to purchasing capabilities, adversaries may steal capabilities from third-party entities (including other adversaries). This can include stealing software licenses, malware, SSL/TLS and code-signing certificates, or raiding closed databases of vulnerabilities or exploits.(Citation: DiginotarCompromise)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Resource Development]] (TA0042)

### Platforms
- PRE

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Pre-compromise\|M1056]] | Pre-compromise | This technique cannot be easily mitigated with preventive controls since it is based on behaviors performed outside of the scope of enterprise defenses and controls. |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Artificial Intelligence\|T1588.007]] | Artificial Intelligence |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Digital Certificates\|T1588.004]] | Digital Certificates |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Vulnerabilities\|T1588.006]] | Vulnerabilities |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Malware\|T1588.001]] | Malware |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Tool\|T1588.002]] | Tool |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Code Signing Certificates\|T1588.003]] | Code Signing Certificates |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Exploits\|T1588.005]] | Exploits |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1588
- NationsBuying: https://www.nytimes.com/2013/07/14/world/europe/nations-buying-as-hackers-sell-computer-flaws.html
- PegasusCitizenLab: https://citizenlab.ca/2016/08/million-dollar-dissident-iphone-zero-day-nso-group-uae/
- DiginotarCompromise: https://threatpost.com/final-report-diginotar-hack-shows-total-compromise-ca-servers-103112/77170/
- FireEyeSupplyChain: https://www.mandiant.com/resources/supply-chain-analysis-from-quartermaster-to-sunshop
- Analyzing CS Dec 2020: https://www.randhome.io/blog/2020/12/20/analyzing-cobalt-strike-for-fun-and-profit/
- Splunk Kovar Certificates 2017: https://www.splunk.com/en_us/blog/security/tall-tales-of-hunting-with-tls-ssl-certificates.html
- Recorded Future Beacon Certificates: https://www.recordedfuture.com/cobalt-strike-servers/
