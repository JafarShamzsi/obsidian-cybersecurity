---
alias: T1144
---

## T1144

In macOS and OS X, when applications or programs are downloaded from the internet, there is a special attribute set on the file called <code>com.apple.quarantine</code>. This attribute is read by Apple's Gatekeeper defense program at execution time and provides a prompt to the user to allow or deny execution. 

Apps loaded onto the system from USB flash drive, optical disk, external hard drive, or even from a drive shared over the local network won’t set this flag. Additionally, other utilities or events like drive-by downloads don’t necessarily set it either. This completely bypasses the built-in Gatekeeper check. (Citation: Methods of Mac Malware Persistence) The presence of the quarantine flag can be checked by the xattr command <code>xattr /path/to/MyApp.app</code> for <code>com.apple.quarantine</code>. Similarly, given sudo access or elevated permission, this attribute can be removed with xattr as well, <code>sudo xattr -r -d com.apple.quarantine /path/to/MyApp.app</code>. (Citation: Clearing quarantine attribute) (Citation: OceanLotus for OS X)
 
In typical operation, a file will be downloaded from the internet and given a quarantine flag before being saved to disk. When the user tries to open the file or application, macOS’s gatekeeper will step in and check for the presence of this flag. If it exists, then macOS will then prompt the user to confirmation that they want to run the program and will even provide the URL where the application came from. However, this is all based on the file being downloaded from a quarantine-savvy application. (Citation: Bypassing Gatekeeper)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- macOS

### Permissions Required
- User
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | System settings can prevent applications from running that haven't been downloaded through the Apple Store which can help mitigate some of these issues. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1144
- Methods of Mac Malware Persistence: https://www.virusbulletin.com/uploads/pdf/conference/vb2014/VB2014-Wardle.pdf
- Clearing quarantine attribute: https://derflounder.wordpress.com/2012/11/20/clearing-the-quarantine-extended-attribute-from-downloaded-applications/
- OceanLotus for OS X: https://www.alienvault.com/blogs/labs-research/oceanlotus-for-os-x-an-application-bundle-pretending-to-be-an-adobe-flash-update
- Bypassing Gatekeeper: https://blog.malwarebytes.com/cybercrime/2015/10/bypassing-apples-gatekeeper/
