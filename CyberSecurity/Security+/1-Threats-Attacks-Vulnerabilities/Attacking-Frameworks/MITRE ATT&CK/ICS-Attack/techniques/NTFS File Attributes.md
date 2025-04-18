---
alias: T1096
---

## T1096

Every New Technology File System (NTFS) formatted partition contains a Master File Table (MFT) that maintains a record for every file/directory on the partition. (Citation: SpectorOps Host-Based Jul 2017) Within MFT entries are file attributes, (Citation: Microsoft NTFS File Attributes Aug 2010) such as Extended Attributes (EA) and Data [known as Alternate Data Streams (ADSs) when more than one Data attribute is present], that can be used to store arbitrary data (and even complete files). (Citation: SpectorOps Host-Based Jul 2017) (Citation: Microsoft File Streams) (Citation: MalwareBytes ADS July 2015) (Citation: Microsoft ADS Mar 2014)

Adversaries may store malicious data or binaries in file attribute metadata instead of directly in files. This may be done to evade some defenses, such as static indicator scanning tools and anti-virus. (Citation: Journey into IR ZeroAccess NTFS EA) (Citation: MalwareBytes ADS July 2015)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Windows

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Consider adjusting read and write permissions for NTFS EA, though this should be tested to ensure routine OS operations are not impeded. (Citation: InsiderThreat NTFS EA Oct 2017) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1096
- SpectorOps Host-Based Jul 2017: https://posts.specterops.io/host-based-threat-modeling-indicator-design-a9dbbb53d5ea
- Microsoft NTFS File Attributes Aug 2010: https://blogs.technet.microsoft.com/askcore/2010/08/25/ntfs-file-attributes/
- Microsoft File Streams: http://msdn.microsoft.com/en-us/library/aa364404
- MalwareBytes ADS July 2015: https://blog.malwarebytes.com/101/2015/07/introduction-to-alternate-data-streams/
- Microsoft ADS Mar 2014: https://blogs.technet.microsoft.com/askcore/2013/03/24/alternate-data-streams-in-ntfs/
- Journey into IR ZeroAccess NTFS EA: http://journeyintoir.blogspot.com/2012/12/extracting-zeroaccess-from-ntfs.html
- Oddvar Moe ADS1 Jan 2018: https://oddvar.moe/2018/01/14/putting-data-in-alternate-data-streams-and-how-to-execute-it/
- Oddvar Moe ADS2 Apr 2018: https://oddvar.moe/2018/04/11/putting-data-in-alternate-data-streams-and-how-to-execute-it-part-2/
- Symantec ADS May 2009: https://www.symantec.com/connect/articles/what-you-need-know-about-alternate-data-streams-windows-your-data-secure-can-you-restore
