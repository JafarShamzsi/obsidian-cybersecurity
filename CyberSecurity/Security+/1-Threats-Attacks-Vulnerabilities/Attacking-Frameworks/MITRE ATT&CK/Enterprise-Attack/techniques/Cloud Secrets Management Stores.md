---
alias: T1555.006
---

## T1555.006

Adversaries may acquire credentials from cloud-native secret management solutions such as AWS Secrets Manager, GCP Secret Manager, Azure Key Vault, and Terraform Vault.  

Secrets managers support the secure centralized management of passwords, API keys, and other credential material. Where secrets managers are in use, cloud services can dynamically acquire credentials via API requests rather than accessing secrets insecurely stored in plain text files or environment variables.  

If an adversary is able to gain sufficient privileges in a cloud environment – for example, by obtaining the credentials of high-privileged [Cloud Accounts](https://attack.mitre.org/techniques/T1078/004) or compromising a service that has permission to retrieve secrets – they may be able to request secrets from the secrets manager. This can be accomplished via commands such as `get-secret-value` in AWS, `gcloud secrets describe` in GCP, and `az key vault secret show` in Azure.(Citation: Permiso Scattered Spider 2023)(Citation: Sysdig ScarletEel 2.0 2023)(Citation: AWS Secrets Manager)(Citation: Google Cloud Secrets)(Citation: Microsoft Azure Key Vault)

**Note:** this technique is distinct from [Cloud Instance Metadata API](https://attack.mitre.org/techniques/T1552/005) in that the credentials are being directly requested from the cloud secrets manager, rather than through the medium of the instance metadata API.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- IaaS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Limit the number of cloud accounts and services with permission to query the secrets manager to only those required. Ensure that accounts and services with permissions to query the secrets manager only have access to the secrets they require. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1555/006
- Sysdig ScarletEel 2.0 2023: https://sysdig.com/blog/scarleteel-2-0/
- AWS Secrets Manager: https://docs.aws.amazon.com/secretsmanager/latest/userguide/retrieving-secrets.html
- Google Cloud Secrets: https://cloud.google.com/secret-manager/docs/view-secret-details
- Permiso Scattered Spider 2023: https://permiso.io/blog/lucr-3-scattered-spider-getting-saas-y-in-the-cloud
- Microsoft Azure Key Vault: https://learn.microsoft.com/en-us/azure/key-vault/secrets/quick-create-cli
