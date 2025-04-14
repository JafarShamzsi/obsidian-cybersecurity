---
alias: T1567.004
---

## T1567.004

Adversaries may exfiltrate data to a webhook endpoint rather than over their primary command and control channel. Webhooks are simple mechanisms for allowing a server to push data over HTTP/S to a client without the need for the client to continuously poll the server.(Citation: RedHat Webhooks) Many public and commercial services, such as Discord, Slack, and `webhook.site`, support the creation of webhook endpoints that can be used by other services, such as Github, Jira, or Trello.(Citation: Discord Intro to Webhooks) When changes happen in the linked services (such as pushing a repository update or modifying a ticket), these services will automatically post the data to the webhook endpoint for use by the consuming application. 

Adversaries may link an adversary-owned environment to a victim-owned SaaS service to achieve repeated [Automated Exfiltration](https://attack.mitre.org/techniques/T1020) of emails, chat messages, and other data.(Citation: Push Security SaaS Attacks Repository Webhooks) Alternatively, instead of linking the webhook endpoint to a service, an adversary can manually post staged data directly to the URL in order to exfiltrate it.(Citation: Microsoft SQL Server)

Access to webhook endpoints is often over HTTPS, which gives the adversary an additional level of protection. Exfiltration leveraging webhooks can also blend in with normal network traffic if the webhook endpoint points to a commonly used SaaS application or collaboration service.(Citation: CyberArk Labs Discord)(Citation: Talos Discord Webhook Abuse)(Citation: Checkmarx Webhooks)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Exfiltration]] (TA0010)

### Platforms
- Windows
- macOS
- Linux
- SaaS
- Office 365
- Google Workspace

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Data Loss Prevention\|M1057]] | Data Loss Prevention | Data loss prevention can be detect and block sensitive data being uploaded to web services via web browsers. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1567/004
- Checkmarx Webhooks: https://medium.com/checkmarx-security/webhook-party-malicious-packages-caught-exfiltrating-data-via-legit-webhook-services-6e046b07d191
- CyberArk Labs Discord: https://www.cyberark.com/resources/threat-research-blog/the-not-so-secret-war-on-discord
- Discord Intro to Webhooks: https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks
- Microsoft SQL Server: https://www.microsoft.com/security/blog/2023/10/03/defending-new-vectors-threat-actors-attempt-sql-server-to-cloud-lateral-movement/
- Talos Discord Webhook Abuse: https://blog.talosintelligence.com/collab-app-abuse/
- Push Security SaaS Attacks Repository Webhooks: https://github.com/pushsecurity/saas-attacks/blob/main/techniques/webhooks/description.md
- RedHat Webhooks: https://www.redhat.com/en/topics/automation/what-is-a-webhook
