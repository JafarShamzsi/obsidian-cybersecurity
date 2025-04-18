---
alias: T1069.003
---

## T1069.003

Adversaries may attempt to find cloud groups and permission settings. The knowledge of cloud permission groups can help adversaries determine the particular roles of users and groups within an environment, as well as which users are associated with a particular group.

With authenticated access there are several tools that can be used to find permissions groups. The <code>Get-MsolRole</code> PowerShell cmdlet can be used to obtain roles and permissions groups for Exchange and Office 365 accounts (Citation: Microsoft Msolrole)(Citation: GitHub Raindance).

Azure CLI (AZ CLI) and the Google Cloud Identity Provider API also provide interfaces to obtain permissions groups. The command <code>az ad user get-member-groups</code> will list groups associated to a user account for Azure while the API endpoint <code>GET https://cloudidentity.googleapis.com/v1/groups</code> lists group resources available to a user for Google.(Citation: Microsoft AZ CLI)(Citation: Black Hills Red Teaming MS AD Azure, 2018)(Citation: Google Cloud Identity API Documentation) In AWS, the commands `ListRolePolicies` and `ListAttachedRolePolicies` allow users to enumerate the policies attached to a role.(Citation: Palo Alto Unit 42 Compromised Cloud Compute Credentials 2022)

Adversaries may attempt to list ACLs for objects to determine the owner and other accounts with access to the object, for example, via the AWS <code>GetBucketAcl</code> API (Citation: AWS Get Bucket ACL). Using this information an adversary can target accounts with permissions to a given object or leverage accounts they have already compromised to access the object.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Discovery]] (TA0007)

### Platforms
- Azure AD
- Office 365
- SaaS
- IaaS
- Google Workspace

### Permissions Required

### Mitigations


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1069/003
- AWS Get Bucket ACL: https://docs.aws.amazon.com/AmazonS3/latest/API/API_GetBucketAcl.html
- Palo Alto Unit 42 Compromised Cloud Compute Credentials 2022: https://unit42.paloaltonetworks.com/compromised-cloud-compute-credentials/
- Black Hills Red Teaming MS AD Azure, 2018: https://www.blackhillsinfosec.com/red-teaming-microsoft-part-1-active-directory-leaks-via-azure/
- Google Cloud Identity API Documentation: https://cloud.google.com/identity/docs/reference/rest
- Microsoft AZ CLI: https://docs.microsoft.com/en-us/cli/azure/ad/user?view=azure-cli-latest
- Microsoft Msolrole: https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolrole?view=azureadps-1.0
- GitHub Raindance: https://github.com/True-Demon/raindance
