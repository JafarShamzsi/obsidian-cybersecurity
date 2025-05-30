---
alias: T1574.006
---

## T1574.006

Adversaries may execute their own malicious payloads by hijacking environment variables the dynamic linker uses to load shared libraries. During the execution preparation phase of a program, the dynamic linker loads specified absolute paths of shared libraries from environment variables and files, such as <code>LD_PRELOAD</code> on Linux or <code>DYLD_INSERT_LIBRARIES</code> on macOS. Libraries specified in environment variables are loaded first, taking precedence over system libraries with the same function name.(Citation: Man LD.SO)(Citation: TLDP Shared Libraries)(Citation: Apple Doco Archive Dynamic Libraries) These variables are often used by developers to debug binaries without needing to recompile, deconflict mapped symbols, and implement custom functions without changing the original library.(Citation: Baeldung LD_PRELOAD)

On Linux and macOS, hijacking dynamic linker variables may grant access to the victim process's memory, system/network resources, and possibly elevated privileges. This method may also evade detection from security products since the execution is masked under a legitimate process. Adversaries can set environment variables via the command line using the <code>export</code> command, <code>setenv</code> function, or <code>putenv</code> function. Adversaries can also leverage [Dynamic Linker Hijacking](https://attack.mitre.org/techniques/T1574/006) to export variables in a shell or set variables programmatically using higher level syntax such Python’s <code>os.environ</code>.

On Linux, adversaries may set <code>LD_PRELOAD</code> to point to malicious libraries that match the name of legitimate libraries which are requested by a victim program, causing the operating system to load the adversary's malicious code upon execution of the victim program. <code>LD_PRELOAD</code> can be set via the environment variable or <code>/etc/ld.so.preload</code> file.(Citation: Man LD.SO)(Citation: TLDP Shared Libraries) Libraries specified by <code>LD_PRELOAD</code> are loaded and mapped into memory by <code>dlopen()</code> and <code>mmap()</code> respectively.(Citation: Code Injection on Linux and macOS)(Citation: Uninformed Needle) (Citation: Phrack halfdead 1997)(Citation: Brown Exploiting Linkers) 

On macOS this behavior is conceptually the same as on Linux, differing only in how the macOS dynamic libraries (dyld) is implemented at a lower level. Adversaries can set the <code>DYLD_INSERT_LIBRARIES</code> environment variable to point to malicious libraries containing names of legitimate libraries or functions requested by a victim program.(Citation: TheEvilBit DYLD_INSERT_LIBRARIES)(Citation: Timac DYLD_INSERT_LIBRARIES)(Citation: Gabilondo DYLD_INSERT_LIBRARIES Catalina Bypass) 


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Operating System Configuration\|M1028]] | Operating System Configuration | When System Integrity Protection (SIP) is enabled in macOS, the aforementioned environment variables are ignored when executing protected binaries. Third-party applications can also leverage Apple’s Hardened Runtime, ensuring these environment variables are subject to imposed restrictions.(Citation: Apple Developer Doco Hardened Runtime) Admins can add restrictions to applications by setting the setuid and/or setgid bits, use entitlements, or have a __RESTRICT segment in the Mach-O binary. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Adversaries may use new payloads to execute this technique. Identify and block potentially malicious software executed through hijacking by using application control solutions also capable of blocking libraries loaded by legitimate software. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1574/006
- Man LD.SO: https://www.man7.org/linux/man-pages/man8/ld.so.8.html
- TLDP Shared Libraries: https://www.tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html
- Apple Doco Archive Dynamic Libraries: https://developer.apple.com/library/archive/documentation/DeveloperTools/Conceptual/DynamicLibraries/100-Articles/OverviewOfDynamicLibraries.html
- Baeldung LD_PRELOAD: https://www.baeldung.com/linux/ld_preload-trick-what-is
- Code Injection on Linux and macOS: https://www.datawire.io/code-injection-on-linux-and-macos/
- Uninformed Needle: http://hick.org/code/skape/papers/needle.txt
- Phrack halfdead 1997: http://phrack.org/issues/51/8.html
- Brown Exploiting Linkers: http://www.nth-dimension.org.uk/pub/BTL.pdf
- TheEvilBit DYLD_INSERT_LIBRARIES: https://theevilbit.github.io/posts/dyld_insert_libraries_dylib_injection_in_macos_osx_deep_dive/
- Timac DYLD_INSERT_LIBRARIES: https://blog.timac.org/2012/1218-simple-code-injection-using-dyld_insert_libraries/
- Gabilondo DYLD_INSERT_LIBRARIES Catalina Bypass: https://jon-gabilondo-angulo-7635.medium.com/how-to-inject-code-into-mach-o-apps-part-ii-ddb13ebc8191
