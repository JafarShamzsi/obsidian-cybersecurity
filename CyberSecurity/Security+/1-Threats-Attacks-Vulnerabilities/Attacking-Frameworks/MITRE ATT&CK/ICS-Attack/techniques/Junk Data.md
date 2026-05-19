---
alias: T1001.001
---

## T1001.001

Adversaries may add junk data to protocols used for command and control to make detection more difficult.(Citation: FireEye SUNBURST Backdoor December 2020) By adding random or meaningless data to the protocols used for command and control, adversaries can prevent trivial methods for decoding, deciphering, or otherwise analyzing the traffic. Examples may include appending/prepending data with junk characters or writing junk characters between significant characters. 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Command and Control]] (TA0011)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Network intrusion detection and prevention systems that use network signatures to identify traffic for specific adversary malware can be used to mitigate some obfuscation activity at the network level.  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1001/001
- FireEye SUNBURST Backdoor December 2020: https://www.fireeye.com/blog/threat-research/2020/12/evasive-attacker-leverages-solarwinds-supply-chain-compromises-with-sunburst-backdoor.html
- University of Birmingham C2: https://arxiv.org/ftp/arxiv/papers/1408/1408.1136.pdf
