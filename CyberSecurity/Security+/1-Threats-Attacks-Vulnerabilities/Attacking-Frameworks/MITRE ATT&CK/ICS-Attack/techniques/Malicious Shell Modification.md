---
alias: T1156
---

## T1156

Adversaries may establish persistence through executing malicious commands triggered by a user’s shell. User shells execute several configuration scripts at different points throughout the session based on events. For example, when a user opens a command line interface or remotely logs in (such as SSH) a login shell is initiated. The login shell executes scripts from the system (/etc) and the user’s home directory (~/) to configure the environment. All login shells on a system use <code>/etc/profile</code> when initiated. These configuration scripts run at the permission level of their directory and are often used to set environment variables, create aliases, and customize the user’s environment. When the shell exits or terminates, additional shell scripts are executed to ensure the shell exits appropriately. 

Adversaries may attempt to establish persistence by inserting commands into scripts automatically executed by shells. Using bash as an example, the default shell for most GNU/Linux systems, adversaries may add commands that launch malicious binaries into the <code>/etc/profile</code> and <code>/etc/profile.d</code> files (Citation: intezer-kaiji-malware). These files require root permissions and are executed each time any shell on a system launches. For user level permissions, adversaries can insert malicious commands into <code>~/.bash_profile</code>, <code>~/.bash_login</code>, or <code>~/.profile</code> (Rocke) which are sourced when a user opens a command line interface or connects remotely. Adversaries often use ~/.bash_profile since the system only executes the first file that exists in the listed order. Adversaries have also leveraged the <code>~/.bashrc</code> file (Tsunami, Rocke, Linux Rabbit, Magento) which is additionally executed if the connection is established remotely or an additional interactive shell is opened, such as a new tab in the command line interface. Some malware targets the termination of a program to trigger execution (Cannon), adversaries can use the <code>~/.bash_logout</code> file to execute malicious commands at the end of a session(Pearl_shellbot). 

For macOS, the functionality of this technique is similar but leverages zsh, the default shell for macOS 10.15+. When the Terminal.app is opened, the application launches a zsh login shell and a zsh interactive shell. The login shell configures the system environment using <code>/etc/profile</code>, <code>/etc/zshenv</code>, <code>/etc/zprofile</code>, and <code>/etc/zlogin</code>. The login shell then configures the user environment with <code>~/.zprofile</code> and <code>~/.zlogin</code>. The interactive shell uses the <code>~/.zshrc<code> to configure the user environment. Upon exiting, <code>/etc/zlogout</code> and <code>~/.zlogout</code> are executed. For legacy programs, macOS executes <code>/etc/bashrc</code> on startup.


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Persistence]] (TA0003)

### Platforms
- Linux
- macOS

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Restrict File and Directory Permissions\|M1022]] | Restrict File and Directory Permissions | Making these files immutable and only changeable by certain administrators will limit the ability for adversaries to easily create user level persistence. |

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1156
- intezer-kaiji-malware: https://www.intezer.com/blog/research/kaiji-new-chinese-linux-malware-turning-to-golang/
