---
alias: T1619
---

## T1619

Adversaries may enumerate objects in cloud storage infrastructure. Adversaries may use this information during automated discovery to shape follow-on behaviors, including requesting all or specific objects from cloud storage.  Similar to [File and Directory Discovery](https://attack.mitre.org/techniques/T1083) on a local host, after identifying available storage services (i.e. [Cloud Infrastructure Discovery](https://attack.mitre.org/techniques/T1580)) adversaries may access the contents/objects stored in cloud infrastructure.

Cloud service providers offer APIs allowing users to enumerate objects stored within cloud storage. Examples include ListObjectsV2 in AWS (Citation: ListObjectsV2) and List Blobs in Azure(Citation: List Blobs) .


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Discovery]] (TA0007)

### Platforms
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Restrict granting of permissions related to listing objects in cloud storage to necessary accounts. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1619
- ListObjectsV2: https://docs.aws.amazon.com/AmazonS3/latest/API/API_ListObjectsV2.html
- List Blobs: https://docs.microsoft.com/en-us/rest/api/storageservices/list-blobs
