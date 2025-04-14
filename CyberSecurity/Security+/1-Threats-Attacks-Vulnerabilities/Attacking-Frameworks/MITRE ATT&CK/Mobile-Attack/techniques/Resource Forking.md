---
alias: T1564.009
---

## T1564.009

Adversaries may abuse resource forks to hide malicious code or executables to evade detection and bypass security applications. A resource fork provides applications a structured way to store resources such as thumbnail images, menu definitions, icons, dialog boxes, and code.(Citation: macOS Hierarchical File System Overview) Usage of a resource fork is identifiable when displaying a file’s extended attributes, using <code>ls -l@</code> or <code>xattr -l</code> commands. Resource forks have been deprecated and replaced with the application bundle structure. Non-localized resources are placed at the top level directory of an application bundle, while localized resources are placed in the <code>/Resources</code> folder.(Citation: Resource and Data Forks)(Citation: ELC Extended Attributes)

Adversaries can use resource forks to hide malicious data that may otherwise be stored directly in files. Adversaries can execute content with an attached resource fork, at a specified offset, that is moved to an executable location then invoked. Resource fork content may also be obfuscated/encrypted until execution.(Citation: sentinellabs resource named fork 2020)(Citation: tau bundlore erika noerenberg 2020)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Application Developer Guidance\|M1013]] | Application Developer Guidance | Configure applications to use the application bundle structure which leverages the <code>/Resources</code> folder location.(Citation: Apple App Security Overview)  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1564/009
- tau bundlore erika noerenberg 2020: https://blogs.vmware.com/security/2020/06/tau-threat-analysis-bundlore-macos-mm-install-macos.html
- Resource and Data Forks: https://flylib.com/books/en/4.395.1.192/1/
- ELC Extended Attributes: https://eclecticlight.co/2020/10/24/theres-more-to-files-than-data-extended-attributes/
- sentinellabs resource named fork 2020: https://www.sentinelone.com/labs/resourceful-macos-malware-hides-in-named-fork/
- macOS Hierarchical File System Overview: http://tenon.com/products/codebuilder/User_Guide/6_File_Systems.html#anchor520553
