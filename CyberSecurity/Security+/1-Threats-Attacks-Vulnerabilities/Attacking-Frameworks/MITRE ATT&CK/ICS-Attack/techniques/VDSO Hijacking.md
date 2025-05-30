---
alias: T1055.014
---

## T1055.014

Adversaries may inject malicious code into processes via VDSO hijacking in order to evade process-based defenses as well as possibly elevate privileges. Virtual dynamic shared object (vdso) hijacking is a method of executing arbitrary code in the address space of a separate live process. 

VDSO hijacking involves redirecting calls to dynamically linked shared libraries. Memory protections may prevent writing executable code to a process via [Ptrace System Calls](https://attack.mitre.org/techniques/T1055/008). However, an adversary may hijack the syscall interface code stubs mapped into a process from the vdso shared object to execute syscalls to open and map a malicious shared object. This code can then be invoked by redirecting the execution flow of the process via patched memory address references stored in a process' global offset table (which store absolute addresses of mapped library functions).(Citation: ELF Injection May 2009)(Citation: Backtrace VDSO)(Citation: VDSO Aug 2005)(Citation: Syscall 2014)

Running code in the context of another process may allow access to the process's memory, system/network resources, and possibly elevated privileges. Execution via VDSO hijacking may also evade detection from security products since the execution is masked under a legitimate process.  


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Privilege Escalation]] (TA0004)

### Platforms
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Behavior Prevention on Endpoint\|M1040]] | Behavior Prevention on Endpoint | Some endpoint security solutions can be configured to block some types of process injection based on common sequences of behavior that occur during the injection process.  |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1055/014
- Backtrace VDSO: https://backtrace.io/blog/backtrace/elf-shared-library-injection-forensics/
- Syscall 2014: https://lwn.net/Articles/604515/
- GNU Acct: https://www.gnu.org/software/acct/
- RHEL auditd: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/chap-system_auditing
- ELF Injection May 2009: https://web.archive.org/web/20150711051625/http://vxer.org/lib/vrn00.html
- VDSO Aug 2005: https://web.archive.org/web/20051013084246/http://www.trilithium.com/johan/2005/08/linux-gate/
- Chokepoint preload rootkits: http://www.chokepoint.net/2014/02/detecting-userland-preload-rootkits.html
