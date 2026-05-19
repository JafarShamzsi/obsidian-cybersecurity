---
alias: T1537
---

## T1537

Adversaries may exfiltrate data by transferring the data, including through sharing/syncing and creating backups of cloud environments, to another cloud account they control on the same service.

A defender who is monitoring for large transfers to outside the cloud environment through normal file transfers or over command and control channels may not be watching for data transfers to another account within the same cloud provider. Such transfers may utilize existing cloud provider APIs and the internal address space of the cloud provider to blend into normal traffic or avoid data transfers over external network interfaces.(Citation: TLDRSec AWS Attacks)

Adversaries may also use cloud-native mechanisms to share victim data with adversary-controlled cloud accounts, such as creating anonymous file sharing links or, in Azure, a shared access signature (SAS) URI.(Citation: Microsoft Azure Storage Shared Access Signature)

Incidents have been observed where adversaries have created backups of cloud instances and transferred them to separate accounts.(Citation: DOJ GRU Indictment Jul 2018) 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Exfiltration]] (TA0010)

### Platforms
- IaaS
- SaaS
- Google Workspace
- Office 365

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Filter Network Traffic\|M1037]] | Filter Network Traffic | Implement network-based filtering restrictions to prohibit data transfers to untrusted VPCs. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Data Loss Prevention\|M1057]] | Data Loss Prevention | Data loss prevention can prevent and block sensitive data from being shared with individuals outside an organization.(Citation: Microsoft Purview Data Loss Prevention) (Citation: Google Workspace Data Loss Prevention) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Consider rotating access keys within a certain number of days to reduce the effectiveness of stolen credentials. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Limit user account and IAM policies to the least privileges required. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Software Configuration\|M1054]] | Software Configuration | Configure appropriate data sharing restrictions in cloud services. For example, external sharing in Microsoft SharePoint and Google Drive can be turned off altogether, blocked for certain domains, or restricted to certain users.(Citation: Google Workspace External Sharing) (Citation: Microsoft 365 External Sharing) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1537
- AWS EBS Snapshot Sharing: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-modifying-snapshot-permissions.html
- TLDRSec AWS Attacks: https://tldrsec.com/p/blog-lesser-known-aws-attacks
- Azure Shared Access Signature: https://docs.microsoft.com/en-us/rest/api/storageservices/delegate-access-with-shared-access-signature
- Azure Blob Snapshots: https://docs.microsoft.com/en-us/azure/storage/blobs/snapshots-overview
- Microsoft Azure Storage Shared Access Signature: https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview
- DOJ GRU Indictment Jul 2018: https://www.justice.gov/file/1080281/download
