---
alias: T1620
---

## T1620

Adversaries may reflectively load code into a process in order to conceal the execution of malicious payloads. Reflective loading involves allocating then executing payloads directly within the memory of the process, vice creating a thread or process backed by a file path on disk (e.g., [Shared Modules](https://attack.mitre.org/techniques/T1129)).

Reflectively loaded payloads may be compiled binaries, anonymous files (only present in RAM), or just snubs of fileless executable code (ex: position-independent shellcode).(Citation: Introducing Donut)(Citation: S1 Custom Shellcode Tool)(Citation: Stuart ELF Memory)(Citation: 00sec Droppers)(Citation: Mandiant BYOL) For example, the `Assembly.Load()` method executed by [PowerShell](https://attack.mitre.org/techniques/T1059/001) may be abused to load raw code into the running process.(Citation: Microsoft AssemblyLoad)

Reflective code injection is very similar to [Process Injection](https://attack.mitre.org/techniques/T1055) except that the “injection” loads code into the processes’ own memory instead of that of a separate process. Reflective loading may evade process-based detections since the execution of the arbitrary code may be masked within a legitimate or otherwise benign process. Reflectively loading payloads directly into memory may also avoid creating files or other artifacts on disk, while also enabling malware to keep these payloads encrypted (or otherwise obfuscated) until execution.(Citation: Stuart ELF Memory)(Citation: 00sec Droppers)(Citation: Intezer ACBackdoor)(Citation: S1 Old Rat New Tricks)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- macOS
- Linux
- Windows

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1620
- 00sec Droppers: https://0x00sec.org/t/super-stealthy-droppers/3715
- S1 Custom Shellcode Tool: https://www.sentinelone.com/blog/building-a-custom-tool-for-shellcode-analysis/
- Mandiant BYOL: https://www.mandiant.com/resources/bring-your-own-land-novel-red-teaming-technique
- S1 Old Rat New Tricks: https://www.sentinelone.com/blog/teaching-an-old-rat-new-tricks/
- MDSec Detecting DOTNET: https://www.mdsec.co.uk/2020/06/detecting-and-advancing-in-memory-net-tradecraft/
- Microsoft AssemblyLoad: https://learn.microsoft.com/dotnet/api/system.reflection.assembly.load
- Intezer ACBackdoor: https://www.intezer.com/blog/research/acbackdoor-analysis-of-a-new-multiplatform-backdoor/
- Stuart ELF Memory: https://magisterquis.github.io/2018/03/31/in-memory-only-elf-execution.html
- Introducing Donut: https://thewover.github.io/Introducing-Donut/
