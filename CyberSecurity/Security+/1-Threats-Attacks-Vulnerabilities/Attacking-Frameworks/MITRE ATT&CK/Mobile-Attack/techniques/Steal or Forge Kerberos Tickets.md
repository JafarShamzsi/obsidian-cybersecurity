---
alias: T1558
---

## T1558

Adversaries may attempt to subvert Kerberos authentication by stealing or forging Kerberos tickets to enable [Pass the Ticket](https://attack.mitre.org/techniques/T1550/003). Kerberos is an authentication protocol widely used in modern Windows domain environments. In Kerberos environments, referred to as “realms”, there are three basic participants: client, service, and Key Distribution Center (KDC).(Citation: ADSecurity Kerberos Ring Decoder) Clients request access to a service and through the exchange of Kerberos tickets, originating from KDC, they are granted access after having successfully authenticated. The KDC is responsible for both authentication and ticket granting.  Adversaries may attempt to abuse Kerberos by stealing tickets or forging tickets to enable unauthorized access.

On Windows, the built-in <code>klist</code> utility can be used to list and analyze cached Kerberos tickets.(Citation: Microsoft Klist)

Linux systems on Active Directory domains store Kerberos credentials locally in the credential cache file referred to as the "ccache". The credentials are stored in the ccache file while they remain valid and generally while a user's session lasts.(Citation: MIT ccache) On modern Redhat Enterprise Linux systems, and derivative distributions, the System Security Services Daemon (SSSD) handles Kerberos tickets. By default SSSD maintains a copy of the ticket database that can be found in <code>/var/lib/sss/secrets/secrets.ldb</code> as well as the corresponding key located in <code>/var/lib/sss/secrets/.secrets.mkey</code>. Both files require root access to read. If an adversary is able to access the database and key, the credential cache Kerberos blob can be extracted and converted into a usable Kerberos ccache file that adversaries may use for [Pass the Ticket](https://attack.mitre.org/techniques/T1550/003). The ccache file may also be converted into a Windows format using tools such as Kekeo.(Citation: Linux Kerberos Tickets)(Citation: Brining MimiKatz to Unix)(Citation: Kekeo)


Kerberos tickets on macOS are stored in a standard ccache format, similar to Linux. By default, access to these ccache entries is federated through the KCM daemon process via the Mach RPC protocol, which uses the caller's environment to determine access. The storage location for these ccache entries is influenced by the <code>/etc/krb5.conf</code> configuration file and the <code>KRB5CCNAME</code> environment variable which can specify to save them to disk or keep them protected via the KCM daemon. Users can interact with ticket storage using <code>kinit</code>, <code>klist</code>, <code>ktutil</code>, and <code>kcc</code> built-in binaries or via Apple's native Kerberos framework. Adversaries can use open source tools to interact with the ccache files directly or to use the Kerberos framework to call lower-level APIs for extracting the user's TGT or Service Tickets.(Citation: SpectorOps Bifrost Kerberos macOS 2019)(Citation: macOS kerberos framework MIT)



### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows
- Linux
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Password Policies\|M1027]] | Password Policies | Ensure strong password length (ideally 25+ characters) and complexity for service accounts and that these passwords periodically expire.(Citation: AdSecurity Cracking Kerberos Dec 2015) Also consider using Group Managed Service Accounts or another third party product such as password vaulting.(Citation: AdSecurity Cracking Kerberos Dec 2015) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Privileged Account Management\|M1026]] | Privileged Account Management | Limit domain admin account permissions to domain controllers and limited servers. Delegate other admin functions to separate accounts.<br /><br />Limit service accounts to minimal required privileges, including membership in privileged groups such as Domain Administrators.(Citation: AdSecurity Cracking Kerberos Dec 2015) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Audit\|M1047]] | Audit | Perform audits or scans of systems, permissions, insecure software, insecure configurations, etc. to identify potential weaknesses. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Active Directory Configuration\|M1015]] | Active Directory Configuration | For containing the impact of a previously generated golden ticket, reset the built-in KRBTGT account password twice, which will invalidate any existing golden tickets that have been created with the KRBTGT hash and other Kerberos tickets derived from it. For each domain, change the KRBTGT account password once, force replication, and then change the password a second time. Consider rotating the KRBTGT account password every 180 days.(Citation: STIG krbtgt reset) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Encrypt Sensitive Information\|M1041]] | Encrypt Sensitive Information | Enable AES Kerberos encryption (or another stronger encryption algorithm), rather than RC4, where possible.(Citation: AdSecurity Cracking Kerberos Dec 2015) |

### Sub-techniques

| ID | Name |
| --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/AS-REP Roasting\|T1558.004]] | AS-REP Roasting |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Golden Ticket\|T1558.001]] | Golden Ticket |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Silver Ticket\|T1558.002]] | Silver Ticket |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/techniques/Kerberoasting\|T1558.003]] | Kerberoasting |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1558
- CERT-EU Golden Ticket Protection: https://cert.europa.eu/static/WhitePapers/UPDATED%20-%20CERT-EU_Security_Whitepaper_2014-007_Kerberos_Golden_Ticket_Protection_v1_4.pdf
- Microsoft Detecting Kerberoasting Feb 2018: https://blogs.technet.microsoft.com/motiba/2018/02/23/detecting-kerberoasting-activity-using-azure-security-center/
- Kekeo: https://github.com/gentilkiwi/kekeo
- SpectorOps Bifrost Kerberos macOS 2019: https://posts.specterops.io/when-kirbi-walks-the-bifrost-4c727807744f
- Medium Detecting Attempts to Steal Passwords from Memory: https://medium.com/threatpunter/detecting-attempts-to-steal-passwords-from-memory-558f16dce4ea
- Stealthbits Detect PtT 2019: https://blog.stealthbits.com/detect-pass-the-ticket-attacks
- macOS kerberos framework MIT: http://web.mit.edu/macdev/KfM/Common/Documentation/preferences.html
- MIT ccache: https://web.mit.edu/kerberos/krb5-1.12/doc/basic/ccache_def.html
- AdSecurity Cracking Kerberos Dec 2015: https://adsecurity.org/?p=2293
- ADSecurity Detecting Forged Tickets: https://adsecurity.org/?p=1515
- Microsoft Kerberos Golden Ticket: https://gallery.technet.microsoft.com/scriptcenter/Kerberos-Golden-Ticket-b4814285
- Microsoft Klist: https://docs.microsoft.com/windows-server/administration/windows-commands/klist
- ADSecurity Kerberos Ring Decoder: https://adsecurity.org/?p=227
- Brining MimiKatz to Unix: https://labs.portcullis.co.uk/download/eu-18-Wadhwa-Brown-Where-2-worlds-collide-Bringing-Mimikatz-et-al-to-UNIX.pdf
- Linux Kerberos Tickets: https://www.fireeye.com/blog/threat-research/2020/04/kerberos-tickets-on-linux-red-teams.html
