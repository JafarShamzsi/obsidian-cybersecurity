---
alias: T1583.008
---

## T1583.008

Adversaries may purchase online advertisements that can be abused to distribute malware to victims. Ads can be purchased to plant as well as favorably position artifacts in specific locations  online, such as prominently placed within search engine results. These ads may make it more difficult for users to distinguish between actual search results and advertisements.(Citation: spamhaus-malvertising) Purchased ads may also target specific audiences using the advertising network’s capabilities, potentially further taking advantage of the trust inherently given to search engines and popular websites. 

Adversaries may purchase ads and other resources to help distribute artifacts containing malicious code to victims. Purchased ads may attempt to impersonate or spoof well-known brands. For example, these spoofed ads may trick victims into clicking the ad which could then send them to a malicious domain that may be a clone of official websites containing trojanized versions of the advertised software.(Citation: Masquerads-Guardio)(Citation: FBI-search) Adversary’s efforts to create malicious domains and purchase advertisements may also be automated at scale to better resist cleanup efforts.(Citation: sentinelone-malvertising) 

Malvertising may be used to support [Drive-by Target](https://attack.mitre.org/techniques/T1608/004) and [Drive-by Compromise](https://attack.mitre.org/techniques/T1189), potentially requiring limited interaction from the user if the ad contains code/exploits that infect the target system's web browser.(Citation: BBC-malvertising)

Adversaries may also employ several techniques to evade detection by the advertising network. For example, adversaries may dynamically route ad clicks to send automated crawler/policy enforcer traffic to benign sites while validating potential targets then sending victims referred from real ad clicks to malicious pages. This infection vector may therefore remain hidden from the ad network as well as any visitor not reaching the malicious sites with a valid identifier from clicking on the advertisement.(Citation: Masquerads-Guardio) Other tricks, such as intentional typos to avoid brand reputation monitoring, may also be used to evade automated detection.(Citation: spamhaus-malvertising) 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Resource Development]] (TA0042)

### Platforms
- PRE

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Pre-compromise\|M1056]] | Pre-compromise | This technique cannot be easily mitigated with preventive controls since it is based on behaviors performed outside of the scope of enterprise defenses and controls. Efforts should be focused on initial access activities, such as drive by compromise where ad blocking adblockers can help prevent malicious code from executing. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1583/008
- BBC-malvertising: https://www.bbc.com/news/technology-12891182
- FBI-search: https://www.ic3.gov/Media/Y2022/PSA221221
- sentinelone-malvertising: https://www.sentinelone.com/blog/breaking-down-the-seo-poisoning-attack-how-attackers-are-hijacking-search-results/
- spamhaus-malvertising: https://www.spamhaus.com/resource-center/a-surge-of-malvertising-across-google-ads-is-distributing-dangerous-malware/
- Masquerads-Guardio: https://labs.guard.io/masquerads-googles-ad-words-massively-abused-by-threat-actors-targeting-organizations-gpus-42ae73ee8a1e
