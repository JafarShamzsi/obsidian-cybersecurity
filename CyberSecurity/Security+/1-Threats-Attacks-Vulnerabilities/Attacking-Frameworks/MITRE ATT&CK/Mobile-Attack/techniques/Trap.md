---
alias: T1154
---

## T1154

The <code>trap</code> command allows programs and shells to specify commands that will be executed upon receiving interrupt signals. A common situation is a script allowing for graceful termination and handling of common  keyboard interrupts like <code>ctrl+c</code> and <code>ctrl+d</code>. Adversaries can use this to register code to be executed when the shell encounters specific interrupts either to gain execution or as a persistence mechanism. Trap commands are of the following format <code>trap 'command list' signals</code> where "command list" will be executed when "signals" are received.(Citation: Trap Manual)(Citation: Cyberciti Trap Statements)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Execution]] (TA0002)
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Linux
- macOS

### Permissions Required
- User
- Administrator

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1154
- Trap Manual: https://ss64.com/bash/trap.html
- Cyberciti Trap Statements: https://bash.cyberciti.biz/guide/Trap_statement
