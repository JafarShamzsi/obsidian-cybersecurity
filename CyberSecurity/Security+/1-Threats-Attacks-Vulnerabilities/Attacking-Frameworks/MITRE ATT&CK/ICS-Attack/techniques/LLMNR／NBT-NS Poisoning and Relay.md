---
alias: T1171
---

## T1171

Link-Local Multicast Name Resolution (LLMNR) and NetBIOS Name Service (NBT-NS) are Microsoft Windows components that serve as alternate methods of host identification. LLMNR is based upon the Domain Name System (DNS) format and allows hosts on the same local link to perform name resolution for other hosts. NBT-NS identifies systems on a local network by their NetBIOS name. (Citation: Wikipedia LLMNR) (Citation: TechNet NetBIOS)

Adversaries can spoof an authoritative source for name resolution on a victim network by responding to LLMNR (UDP 5355)/NBT-NS (UDP 137) traffic as if they know the identity of the requested host, effectively poisoning the service so that the victims will communicate with the adversary controlled system. If the requested host belongs to a resource that requires identification/authentication, the username and NTLMv2 hash will then be sent to the adversary controlled system. The adversary can then collect the hash information sent over the wire through tools that monitor the ports for traffic or through [Network Sniffing](https://attack.mitre.org/techniques/T1040) and crack the hashes offline through [Brute Force](https://attack.mitre.org/techniques/T1110) to obtain the plaintext passwords. In some cases where an adversary has access to a system that is in the authentication path between systems or when automated scans that use credentials attempt to authenticate to an adversary controlled system, the NTLMv2 hashes can be intercepted and relayed to access and execute code against a target system. The relay step can happen in conjunction with poisoning but may also be independent of it. (Citation: byt3bl33d3r NTLM Relaying)(Citation: Secure Ideas SMB Relay)

Several tools exist that can be used to poison name services within local networks such as NBNSpoof, Metasploit, and [Responder](https://attack.mitre.org/software/S0174). (Citation: GitHub NBNSpoof) (Citation: Rapid7 LLMNR Spoofer) (Citation: GitHub Responder)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Windows

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Filter Network Traffic\|M1037]] | Filter Network Traffic | Use host-based security software to block LLMNR/NetBIOS traffic. Enabling SMB Signing can stop NTLMv2 relay attacks.(Citation: byt3bl33d3r NTLM Relaying)(Citation: Secure Ideas SMB Relay)(Citation: Microsoft SMB Packet Signing) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Disable LLMNR and NetBIOS in local computer security settings or by group policy if they are not needed within an environment. (Citation: ADSecurity Windows Secure Baseline) |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1171
- Wikipedia LLMNR: https://en.wikipedia.org/wiki/Link-Local_Multicast_Name_Resolution
- TechNet NetBIOS: https://technet.microsoft.com/library/cc958811.aspx
- byt3bl33d3r NTLM Relaying: https://byt3bl33d3r.github.io/practical-guide-to-ntlm-relaying-in-2017-aka-getting-a-foothold-in-under-5-minutes.html
- Secure Ideas SMB Relay: https://blog.secureideas.com/2018/04/ever-run-a-relay-why-smb-relays-should-be-on-your-mind.html
- GitHub NBNSpoof: https://github.com/nomex/nbnspoof
- Rapid7 LLMNR Spoofer: https://www.rapid7.com/db/modules/auxiliary/spoof/llmnr/llmnr_response
- GitHub Responder: https://github.com/SpiderLabs/Responder
- Sternsecurity LLMNR-NBTNS: https://www.sternsecurity.com/blog/local-network-attacks-llmnr-and-nbt-ns-poisoning
- GitHub Conveigh: https://github.com/Kevin-Robertson/Conveigh
