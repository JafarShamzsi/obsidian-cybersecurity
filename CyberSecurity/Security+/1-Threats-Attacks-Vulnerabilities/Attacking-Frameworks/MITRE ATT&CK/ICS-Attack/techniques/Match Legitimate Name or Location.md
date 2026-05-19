---
alias: T1036.005
---

## T1036.005

Adversaries may match or approximate the name or location of legitimate files or resources when naming/placing them. This is done for the sake of evading defenses and observation. This may be done by placing an executable in a commonly trusted directory (ex: under System32) or giving it the name of a legitimate, trusted program (ex: svchost.exe). In containerized environments, this may also be done by creating a resource in a namespace that matches the naming convention of a container pod or cluster. Alternatively, a file or container image name given may be a close approximation to legitimate programs/images or something innocuous.

Adversaries may also use the same icon of the file they are trying to mimic.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- Linux
- macOS
- Windows
- Containers

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Use tools that restrict program execution via application control by attributes other than file name for common operating system utilities that are needed. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/techniques/Code Signing\|M1045]] | Code Signing | Require signed binaries and images. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Use file system access controls to protect folders such as C:\Windows\System32. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1036/005
- Twitter ItsReallyNick Masquerading Update: https://twitter.com/ItsReallyNick/status/1055321652777619457
- Docker Images: https://docs.docker.com/engine/reference/commandline/images/
- Elastic Masquerade Ball: https://www.elastic.co/blog/how-hunt-masquerade-ball
