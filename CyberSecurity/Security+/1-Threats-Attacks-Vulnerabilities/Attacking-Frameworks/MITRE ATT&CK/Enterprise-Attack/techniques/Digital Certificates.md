---
alias: T1587.003
---

## T1587.003

Adversaries may create self-signed SSL/TLS certificates that can be used during targeting. SSL/TLS certificates are designed to instill trust. They include information about the key, information about its owner's identity, and the digital signature of an entity that has verified the certificate's contents are correct. If the signature is valid, and the person examining the certificate trusts the signer, then they know they can use that key to communicate with its owner. In the case of self-signing, digital certificates will lack the element of trust associated with the signature of a third-party certificate authority (CA).

Adversaries may create self-signed SSL/TLS certificates that can be used to further their operations, such as encrypting C2 traffic (ex: [Asymmetric Cryptography](https://attack.mitre.org/techniques/T1573/002) with [Web Protocols](https://attack.mitre.org/techniques/T1071/001)) or even enabling [Adversary-in-the-Middle](https://attack.mitre.org/techniques/T1557) if added to the root of trust (i.e. [Install Root Certificate](https://attack.mitre.org/techniques/T1553/004)).

After creating a digital certificate, an adversary may then install that certificate (see [Install Digital Certificate](https://attack.mitre.org/techniques/T1608/003)) on infrastructure under their control.


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

- mitre-attack: https://attack.mitre.org/techniques/T1587/003
- Splunk Kovar Certificates 2017: https://www.splunk.com/en_us/blog/security/tall-tales-of-hunting-with-tls-ssl-certificates.html
