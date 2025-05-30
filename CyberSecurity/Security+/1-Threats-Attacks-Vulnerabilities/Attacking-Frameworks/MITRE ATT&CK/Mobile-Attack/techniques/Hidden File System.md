---
alias: T1564.005
---

## T1564.005

Adversaries may use a hidden file system to conceal malicious activity from users and security tools. File systems provide a structure to store and access data from physical storage. Typically, a user engages with a file system through applications that allow them to access files and directories, which are an abstraction from their physical location (ex: disk sector). Standard file systems include FAT, NTFS, ext4, and APFS. File systems can also contain other structures, such as the Volume Boot Record (VBR) and Master File Table (MFT) in NTFS.(Citation: MalwareTech VFS Nov 2014)

Adversaries may use their own abstracted file system, separate from the standard file system present on the infected system. In doing so, adversaries can hide the presence of malicious components and file input/output from security tools. Hidden file systems, sometimes referred to as virtual file systems, can be implemented in numerous ways. One implementation would be to store a file system in reserved disk space unused by disk structures or standard file system partitions.(Citation: MalwareTech VFS Nov 2014)(Citation: FireEye Bootkits) Another implementation could be for an adversary to drop their own portable partition image as a file on top of the standard file system.(Citation: ESET ComRAT May 2020) Adversaries may also fragment files across the existing file system structure in non-standard ways.(Citation: Kaspersky Equation QA)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows

### Permissions Required
- User
- Administrator

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1564/005
- MalwareTech VFS Nov 2014: https://www.malwaretech.com/2014/11/virtual-file-systems-for-beginners.html
- FireEye Bootkits: https://www.fireeye.com/blog/threat-research/2015/12/fin1-targets-boot-record.html
- ESET ComRAT May 2020: https://www.welivesecurity.com/wp-content/uploads/2020/05/ESET_Turla_ComRAT.pdf
- Kaspersky Equation QA: https://media.kasperskycontenthub.com/wp-content/uploads/sites/43/2018/03/08064459/Equation_group_questions_and_answers.pdf
