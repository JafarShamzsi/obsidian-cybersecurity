---
alias: T1115
---

## T1115

Adversaries may collect data stored in the clipboard from users copying information within or between applications. 

For example, on Windows adversaries can access clipboard data by using <code>clip.exe</code> or <code>Get-Clipboard</code>.(Citation: MSDN Clipboard)(Citation: clip_win_server)(Citation: CISA_AA21_200B) Additionally, adversaries may monitor then replace users’ clipboard with their data (e.g., [Transmitted Data Manipulation](https://attack.mitre.org/techniques/T1565/002)).(Citation: mining_ruby_reversinglabs)

macOS and Linux also have commands, such as <code>pbpaste</code>, to grab clipboard contents.(Citation: Operating with EmPyre)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/Mobile-Attack/tactics/Collection]] (TA0009)

### Platforms
- Linux
- Windows
- macOS

### Permissions Required

### Mitigations

### Sub-techniques


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1115
- CISA_AA21_200B: https://www.cisa.gov/uscert/ncas/alerts/aa21-200b
- mining_ruby_reversinglabs: https://blog.reversinglabs.com/blog/mining-for-malicious-ruby-gems
- clip_win_server: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/clip
- MSDN Clipboard: https://msdn.microsoft.com/en-us/library/ms649012
- Operating with EmPyre: https://medium.com/rvrsh3ll/operating-with-empyre-ea764eda3363
