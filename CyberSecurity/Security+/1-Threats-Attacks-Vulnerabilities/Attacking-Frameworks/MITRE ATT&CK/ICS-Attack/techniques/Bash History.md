---
alias: T1552.003
---

## T1552.003

Adversaries may search the bash command history on compromised systems for insecurely stored credentials. Bash keeps track of the commands users type on the command-line with the "history" utility. Once a user logs out, the history is flushed to the user’s <code>.bash_history</code> file. For each user, this file resides at the same location: <code>~/.bash_history</code>. Typically, this file keeps track of the user’s last 500 commands. Users often type usernames and passwords on the command-line as parameters to programs, which then get saved to this file when they log out. Adversaries can abuse this by looking through the file for potential credentials. (Citation: External to DA, the OS X Way)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Credential Access]] (TA0006)

### Platforms
- Linux
- macOS

### Permissions Required
- User

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Operating System Configuration\|M1028]] | Operating System Configuration | There are multiple methods of preventing a user's command history from being flushed to their .bash_history file, including use of the following commands:<br /><code>set +o history</code> and <code>set -o history</code> to start logging again;<br /><code>unset HISTFILE</code> being added to a user's .bash_rc file; and<br /><code>ln -s /dev/null ~/.bash_history</code> to write commands to <code>/dev/null</code>instead. |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1552/003
- External to DA, the OS X Way: http://www.slideshare.net/StephanBorosh/external-to-da-the-os-x-way
