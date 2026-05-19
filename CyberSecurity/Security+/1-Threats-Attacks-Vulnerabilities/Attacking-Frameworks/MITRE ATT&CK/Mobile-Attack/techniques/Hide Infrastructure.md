---
alias: T1665
---

## T1665

Adversaries may manipulate network traffic in order to hide and evade detection of their C2 infrastructure. This can be accomplished in various ways including by identifying and filtering traffic from defensive tools,(Citation: TA571) masking malicious domains to obfuscate the true destination from both automated scanning tools and security researchers,(Citation: Schema-abuse)(Citation: Facad1ng)(Citation: Browser-updates) and otherwise hiding malicious artifacts to delay discovery and prolong the effectiveness of adversary infrastructure that could otherwise be identified, blocked, or taken down entirely.

C2 networks may include the use of [Proxy](https://attack.mitre.org/techniques/T1090) or VPNs to disguise IP addresses, which can allow adversaries to blend in with normal network traffic and bypass conditional access policies or anti-abuse protections. For example, an adversary may use a virtual private cloud to spoof their IP address to closer align with a victim's IP address ranges. This may also bypass security measures relying on geolocation of the source IP address.(Citation: sysdig)(Citation: Orange Residential Proxies)

Adversaries may also attempt to filter network traffic in order to evade defensive tools in numerous ways, including blocking/redirecting common incident responder or security appliance user agents.(Citation: mod_rewrite)(Citation: SocGholish-update) Filtering traffic based on IP and geo-fencing may also avoid automated sandboxing or researcher activity (i.e., [Virtualization/Sandbox Evasion](https://attack.mitre.org/techniques/T1497)).(Citation: TA571)(Citation: mod_rewrite)

Hiding C2 infrastructure may also be supported by [Resource Development](https://attack.mitre.org/tactics/TA0042) activities such as [Acquire Infrastructure](https://attack.mitre.org/techniques/T1583) and [Compromise Infrastructure](https://attack.mitre.org/techniques/T1584). For example, using widely trusted hosting services or domains such as prominent URL shortening providers or marketing services for C2 networks may enable adversaries to present benign content that later redirects victims to malicious web pages or infrastructure once specific conditions are met.(Citation: StarBlizzard)(Citation: QR-cofense)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Command and Control]] (TA0011)

### Platforms
- macOS
- Windows
- Linux
- Network

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1665
- SocGholish-update: https://www.proofpoint.com/us/blog/threat-insight/part-1-socgholish-very-real-threat-very-fake-update
- TA571: https://www.proofpoint.com/us/blog/threat-insight/security-brief-ta571-delivers-icedid-forked-loader
- mod_rewrite: https://bluescreenofjeff.com/2016-04-12-combatting-incident-responders-with-apache-mod_rewrite/
- Browser-updates: https://www.proofpoint.com/us/blog/threat-insight/are-you-sure-your-browser-date-current-landscape-fake-browser-updates
- StarBlizzard: https://www.microsoft.com/en-us/security/blog/2023/12/07/star-blizzard-increases-sophistication-and-evasion-in-ongoing-attacks/
- QR-cofense: https://cofense.com/blog/major-energy-company-targeted-in-large-qr-code-campaign/
- Schema-abuse: https://www.mandiant.com/resources/blog/url-obfuscation-schema-abuse
- Orange Residential Proxies: https://www.orangecyberdefense.com/global/blog/research/residential-proxies
- Facad1ng: https://github.com/spyboy-productions/Facad1ng
- sysdig: https://sysdig.com/content/c/pf-2023-global-cloud-threat-report?x=u_WFRi&xs=524303#page=1
