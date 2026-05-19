---
alias: T1528
---

## T1528

Adversaries can steal application access tokens as a means of acquiring credentials to access remote systems and resources.

Application access tokens are used to make authorized API requests on behalf of a user or service and are commonly used as a way to access resources in cloud and container-based applications and software-as-a-service (SaaS).(Citation: Auth0 - Why You Should Always Use Access Tokens to Secure APIs Sept 2019)  Adversaries who steal account API tokens in cloud and containerized environments may be able to access data and perform actions with the permissions of these accounts, which can lead to privilege escalation and further compromise of the environment.

For example, in Kubernetes environments, processes running inside a container may communicate with the Kubernetes API server using service account tokens. If a container is compromised, an adversary may be able to steal the container’s token and thereby gain access to Kubernetes API commands.(Citation: Kubernetes Service Accounts)  Similarly, instances within continuous-development / continuous-integration (CI/CD) pipelines will often use API tokens to authenticate to other services for testing and deployment.(Citation: Cider Security Top 10 CICD Security Risks) If these pipelines are compromised, adversaries may be able to steal these tokens and leverage their privileges.

Token theft can also occur through social engineering, in which case user action may be required to grant access. OAuth is one commonly implemented framework that issues tokens to users for access to systems. An application desiring access to cloud-based services or protected APIs can gain entry using OAuth 2.0 through a variety of authorization protocols. An example commonly-used sequence is Microsoft's Authorization Code Grant flow.(Citation: Microsoft Identity Platform Protocols May 2019)(Citation: Microsoft - OAuth Code Authorization flow - June 2019) An OAuth access token enables a third-party application to interact with resources containing user data in the ways requested by the application without obtaining user credentials. 
 
Adversaries can leverage OAuth authorization by constructing a malicious application designed to be granted access to resources with the target user's OAuth token.(Citation: Amnesty OAuth Phishing Attacks, August 2019)(Citation: Trend Micro Pawn Storm OAuth 2017) The adversary will need to complete registration of their application with the authorization server, for example Microsoft Identity Platform using Azure Portal, the Visual Studio IDE, the command-line interface, PowerShell, or REST API calls.(Citation: Microsoft - Azure AD App Registration - May 2019) Then, they can send a [Spearphishing Link](https://attack.mitre.org/techniques/T1566/002) to the target user to entice them to grant access to the application. Once the OAuth access token is granted, the application can gain potentially long-term access to features of the user account through [Application Access Token](https://attack.mitre.org/techniques/T1550/001).(Citation: Microsoft - Azure AD Identity Tokens - Aug 2019)

Application access tokens may function within a limited lifetime, limiting how long an adversary can utilize the stolen token. However, in some cases, adversaries can also steal application refresh tokens(Citation: Auth0 Understanding Refresh Tokens), allowing them to obtain new access tokens without prompting the user.  




### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- SaaS
- Office 365
- Azure AD
- Google Workspace
- Containers

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict Web-Based Content\|M1021]] | Restrict Web-Based Content | Administrators can block end-user consent to OAuth applications, disabling users from authorizing third-party apps through OAuth 2.0 and forcing administrative consent for all requests. They can also block end-user registration of applications by their users, to reduce risk. A Cloud Access Security Broker can also be used to ban applications.<br /><br />Azure offers a couple of enterprise policy settings in the Azure Management Portal that may help:<br /><br />"Users -> User settings -> App registrations: Users can register applications" can be set to "no" to prevent users from registering new applications. <br />"Enterprise applications -> User settings -> Enterprise applications: Users can consent to apps accessing company data on their behalf" can be set to "no" to prevent users from consenting to allow third-party multi-tenant applications |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Training\|M1017]] | User Training | Users need to be trained to not authorize third-party applications they don’t recognize. The user should pay particular attention to the redirect URL: if the URL is a misspelled or convoluted sequence of words related to an expected service or SaaS application, the website is likely trying to spoof a legitimate service. Users should also be cautious about the permissions they are granting to apps. For example, offline access and access to read emails should excite higher suspicions because adversaries can utilize SaaS APIs to discover credentials and other sensitive communications. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/User Account Management\|M1018]] | User Account Management | Enforce role-based access control to limit accounts to the least privileges they require. A Cloud Access Security Broker (CASB) can be used to set usage policies and manage user permissions on cloud applications to prevent access to application access tokens. In Kubernetes applications, set “automountServiceAccountToken: false” in the YAML specification of pods that do not require access to service account tokens.(Citation: Kubernetes Hardening Guide) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Audit\|M1047]] | Audit | Administrators should audit all cloud and container accounts to ensure that they are necessary and that the permissions granted to them are appropriate.  Additionally, administrators should perform an audit of all OAuth applications and the permissions they have been granted to access organizational data. This should be done extensively on all applications in order to establish a baseline, followed up on with periodic audits of new or updated applications. Suspicious applications should be investigated and removed. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1528
- Amnesty OAuth Phishing Attacks, August 2019: https://www.amnesty.org/en/latest/research/2019/08/evolving-phishing-attacks-targeting-journalists-and-human-rights-defenders-from-the-middle-east-and-north-africa/
- Auth0 Understanding Refresh Tokens: https://auth0.com/learn/refresh-tokens/
- Auth0 - Why You Should Always Use Access Tokens to Secure APIs Sept 2019: https://auth0.com/blog/why-should-use-accesstokens-to-secure-an-api/
- Cider Security Top 10 CICD Security Risks: https://www.cidersecurity.io/top-10-cicd-security-risks/
- Trend Micro Pawn Storm OAuth 2017: https://blog.trendmicro.com/trendlabs-security-intelligence/pawn-storm-abuses-open-authentication-advanced-social-engineering-attacks
- Kubernetes Service Accounts: https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/
- Microsoft - Azure AD Identity Tokens - Aug 2019: https://docs.microsoft.com/en-us/azure/active-directory/develop/access-tokens
- Microsoft - Azure AD App Registration - May 2019: https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app
- Microsoft - OAuth Code Authorization flow - June 2019: https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow
- Microsoft Identity Platform Protocols May 2019: https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols
