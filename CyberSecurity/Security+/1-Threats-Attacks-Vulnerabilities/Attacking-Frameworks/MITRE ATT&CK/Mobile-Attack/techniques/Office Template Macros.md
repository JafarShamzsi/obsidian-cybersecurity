---
alias: T1137.001
---

## T1137.001

Adversaries may abuse Microsoft Office templates to obtain persistence on a compromised system. Microsoft Office contains templates that are part of common Office applications and are used to customize styles. The base templates within the application are used each time an application starts. (Citation: Microsoft Change Normal Template)

Office Visual Basic for Applications (VBA) macros (Citation: MSDN VBA in Office) can be inserted into the base template and used to execute code when the respective Office application starts in order to obtain persistence. Examples for both Word and Excel have been discovered and published. By default, Word has a Normal.dotm template created that can be modified to include a malicious macro. Excel does not have a template file created by default, but one can be added that will automatically be loaded.(Citation: enigma0x3 normal.dotm)(Citation: Hexacorn Office Template Macros) Shared templates may also be stored and pulled from remote locations.(Citation: GlobalDotName Jun 2019) 

Word Normal.dotm location:<br>
<code>C:\Users\&lt;username&gt;\AppData\Roaming\Microsoft\Templates\Normal.dotm</code>

Excel Personal.xlsb location:<br>
<code>C:\Users\&lt;username&gt;\AppData\Roaming\Microsoft\Excel\XLSTART\PERSONAL.XLSB</code>

Adversaries may also change the location of the base template to point to their own by hijacking the application's search order, e.g. Word 2016 will first look for Normal.dotm under <code>C:\Program Files (x86)\Microsoft Office\root\Office16\</code>, or by modifying the GlobalDotName registry key. By modifying the GlobalDotName registry key an adversary can specify an arbitrary location, file name, and file extension to use for the template that will be loaded on application startup. To abuse GlobalDotName, adversaries may first need to register the template as a trusted document or place it in a trusted location.(Citation: GlobalDotName Jun 2019) 

An adversary may need to enable macros to execute unrestricted depending on the system or enterprise security policy on use of macros.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Windows
- Office 365

### Permissions Required
- User
- Administrator

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | On Windows 10, enable Attack Surface Reduction (ASR) rules to prevent Office applications from creating child processes and from writing potentially malicious executable content to disk. (Citation: win10_asr) |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Follow Office macro security best practices suitable for your environment. Disable Office VBA macros from executing.<br /><br />Disable Office add-ins. If they are required, follow best practices for securing them by requiring them to be signed and disabling user notification for allowing add-ins. For some add-ins types (WLL, VBA) additional mitigation is likely required as disabling add-ins in the Office Trust Center does not disable WLL nor does it prevent VBA code from executing. (Citation: MRWLabs Office Persistence Add-ins)<br /> |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1137/001
- Microsoft Change Normal Template: https://support.office.com/article/Change-the-Normal-template-Normal-dotm-06de294b-d216-47f6-ab77-ccb5166f98ea
- MSDN VBA in Office: https://msdn.microsoft.com/en-us/vba/office-shared-vba/articles/getting-started-with-vba-in-office
- enigma0x3 normal.dotm: https://enigma0x3.net/2014/01/23/maintaining-access-with-normal-dotm/comment-page-1/
- Hexacorn Office Template Macros: http://www.hexacorn.com/blog/2017/04/19/beyond-good-ol-run-key-part-62/
- GlobalDotName Jun 2019: https://www.221bluestreet.com/post/office-templates-and-globaldotname-a-stealthy-office-persistence-technique
- CrowdStrike Outlook Forms: https://malware.news/t/using-outlook-forms-for-lateral-movement-and-persistence/13746
- Outlook Today Home Page: https://medium.com/@bwtech789/outlook-today-homepage-persistence-33ea9b505943
