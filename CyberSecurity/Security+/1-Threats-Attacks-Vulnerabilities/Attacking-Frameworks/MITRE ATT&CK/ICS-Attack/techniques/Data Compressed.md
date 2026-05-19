---
alias: T1002
---

## T1002

An adversary may compress data (e.g., sensitive documents) that is collected prior to exfiltration in order to make it portable and minimize the amount of data sent over the network. The compression is done separately from the exfiltration channel and is performed using a custom program or algorithm, or a more common compression library or utility such as 7zip, RAR, ZIP, or zlib.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Exfiltration]] (TA0010)

### Platforms
- Linux
- Windows
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Network Intrusion Prevention\|M1031]] | Network Intrusion Prevention | Network intrusion prevention or data loss prevention tools may be set to block specific file types from leaving the network over unencrypted channels. An adversary may move to an encrypted channel or use other mechanisms of encapsulating the traffic in these situations. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1002
- Wikipedia File Header Signatures: https://en.wikipedia.org/wiki/List_of_file_signatures
