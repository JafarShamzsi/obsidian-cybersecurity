---
alias: T1491.002
---

## T1491.002

An adversary may deface systems external to an organization in an attempt to deliver messaging, intimidate, or otherwise mislead an organization or users. [External Defacement](https://attack.mitre.org/techniques/T1491/002) may ultimately cause users to distrust the systems and to question/discredit the system’s integrity. Externally-facing websites are a common victim of defacement; often targeted by adversary and hacktivist groups in order to push a political message or spread propaganda.(Citation: FireEye Cyber Threats to Media Industries)(Citation: Kevin Mandia Statement to US Senate Committee on Intelligence)(Citation: Anonymous Hackers Deface Russian Govt Site) [External Defacement](https://attack.mitre.org/techniques/T1491/002) may be used as a catalyst to trigger events, or as a response to actions taken by an organization or government. Similarly, website defacement may also be used as setup, or a precursor, for future attacks such as [Drive-by Compromise](https://attack.mitre.org/techniques/T1189).(Citation: Trend Micro Deep Dive Into Defacement)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Impact]] (TA0040)

### Platforms
- Windows
- IaaS
- Linux
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Data Backup\|M1053]] | Data Backup | Consider implementing IT disaster recovery plans that contain procedures for taking regular data backups that can be used to restore organizational data.(Citation: Ready.gov IT DRP) Ensure backups are stored off system and is protected from common methods adversaries may use to gain access and destroy the backups to prevent recovery. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1491/002
- FireEye Cyber Threats to Media Industries: https://www.fireeye.com/content/dam/fireeye-www/current-threats/pdfs/ib-entertainment.pdf
- Kevin Mandia Statement to US Senate Committee on Intelligence: https://www.intelligence.senate.gov/sites/default/files/documents/os-kmandia-033017.pdf
- Anonymous Hackers Deface Russian Govt Site: https://torrentfreak.com/anonymous-hackers-deface-russian-govt-site-to-protest-web-blocking-nsfw-180512/
- Trend Micro Deep Dive Into Defacement: https://documents.trendmicro.com/assets/white_papers/wp-a-deep-dive-into-defacement.pdf
