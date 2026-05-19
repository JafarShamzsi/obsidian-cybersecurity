---
alias: T1608.005
---

## T1608.005

Adversaries may put in place resources that are referenced by a link that can be used during targeting. An adversary may rely upon a user clicking a malicious link in order to divulge information (including credentials) or to gain execution, as in [Malicious Link](https://attack.mitre.org/techniques/T1204/001). Links can be used for spearphishing, such as sending an email accompanied by social engineering text to coax the user to actively click or copy and paste a URL into a browser. Prior to a phish for information (as in [Spearphishing Link](https://attack.mitre.org/techniques/T1598/003)) or a phish to gain initial access to a system (as in [Spearphishing Link](https://attack.mitre.org/techniques/T1566/002)), an adversary must set up the resources for a link target for the spearphishing link. 

Typically, the resources for a link target will be an HTML page that may include some client-side script such as [JavaScript](https://attack.mitre.org/techniques/T1059/007) to decide what content to serve to the user. Adversaries may clone legitimate sites to serve as the link target, this can include cloning of login pages of legitimate web services or organization login pages in an effort to harvest credentials during [Spearphishing Link](https://attack.mitre.org/techniques/T1598/003).(Citation: Malwarebytes Silent Librarian October 2020)(Citation: Proofpoint TA407 September 2019) Adversaries may also [Upload Malware](https://attack.mitre.org/techniques/T1608/001) and have the link target point to malware for download/execution by the user.

Adversaries may purchase domains similar to legitimate domains (ex: homoglyphs, typosquatting, different top-level domain, etc.) during acquisition of infrastructure ([Domains](https://attack.mitre.org/techniques/T1583/001)) to help facilitate [Malicious Link](https://attack.mitre.org/techniques/T1204/001).

Links can be written by adversaries to mask the true destination in order to deceive victims by abusing the URL schema and increasing the effectiveness of phishing.(Citation: Kaspersky-masking)(Citation: mandiant-masking)

Adversaries may also use free or paid accounts on link shortening services and Platform-as-a-Service providers to host link targets while taking advantage of the widely trusted domains of those providers to avoid being blocked while redirecting victims to malicious pages.(Citation: Netskope GCP Redirection)(Citation: Netskope Cloud Phishing)(Citation: Intezer App Service Phishing)(Citation: Cofense-redirect) In addition, adversaries may serve a variety of malicious links through uniquely generated URIs/URLs (including one-time, single use links).(Citation: iOS URL Scheme)(Citation: URI)(Citation: URI Use)(Citation: URI Unique) Finally, adversaries may take advantage of the decentralized nature of the InterPlanetary File System (IPFS) to host link targets that are difficult to remove.(Citation: Talos IPFS 2022)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Resource Development]] (TA0042)

### Platforms
- PRE

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Pre-compromise\|M1056]] | Pre-compromise | This technique cannot be easily mitigated with preventive controls since it is based on behaviors performed outside of the scope of enterprise defenses and controls. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1608/005
- Netskope GCP Redirection: https://www.netskope.com/blog/targeted-attacks-abusing-google-cloud-platform-open-redirection
- Netskope Cloud Phishing: https://www.netskope.com/blog/a-big-catch-cloud-phishing-from-google-app-engine-and-azure-app-service
- URI Unique: https://media.defense.gov/2020/Jun/09/2002313081/-1/-1/0/CSI-DETECT-AND-PREVENT-WEB-SHELL-MALWARE-20200422.PDF
- Kaspersky-masking: https://www.kaspersky.com/blog/malicious-redirect-methods/50045/
- Talos IPFS 2022: https://blog.talosintelligence.com/ipfs-abuse/
- Malwarebytes Silent Librarian October 2020: https://blog.malwarebytes.com/malwarebytes-news/2020/10/silent-librarian-apt-phishing-attack/
- URI: https://www.techtarget.com/searchsecurity/tip/Preparing-for-uniform-resource-identifier-URI-exploits
- URI Use: https://www.blackhat.com/presentations/bh-dc-08/McFeters-Rios-Carter/Presentation/bh-dc-08-mcfeters-rios-carter.pdf
- iOS URL Scheme: https://docs.ostorlab.co/kb/IPA_URL_SCHEME_HIJACKING/index.html
- Intezer App Service Phishing: https://www.intezer.com/blog/malware-analysis/kud-i-enter-your-server-new-vulnerabilities-in-microsoft-azure/
- Proofpoint TA407 September 2019: https://www.proofpoint.com/us/threat-insight/post/threat-actor-profile-ta407-silent-librarian
- Cofense-redirect: https://cofense.com/blog/major-energy-company-targeted-in-large-qr-code-campaign/
- mandiant-masking: https://www.mandiant.com/resources/blog/url-obfuscation-schema-abuse
