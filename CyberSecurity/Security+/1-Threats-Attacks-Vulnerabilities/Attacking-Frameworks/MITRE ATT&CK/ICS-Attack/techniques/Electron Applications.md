---
alias: T1218.015
---

## T1218.015

Adversaries may abuse components of the Electron framework to execute malicious code. The Electron framework hosts many common applications such as Signal, Slack, and Microsoft Teams.(Citation: Electron 2) Originally developed by GitHub, Electron is a cross-platform desktop application development framework that employs web technologies like JavaScript, HTML, and CSS.(Citation: Electron 3) The Chromium engine is used to display web content and Node.js runs the backend code.(Citation: Electron 1)

Due to the functional mechanics of Electron (such as allowing apps to run arbitrary commands), adversaries may also be able to perform malicious functions in the background potentially disguised as legitimate tools within the framework.(Citation: Electron 1) For example, the abuse of `teams.exe` and `chrome.exe` may allow adversaries to execute malicious commands as child processes of the legitimate application (e.g., `chrome.exe --disable-gpu-sandbox --gpu-launcher="C:\Windows\system32\cmd.exe /c calc.exe`).(Citation: Electron 6-8)

Adversaries may also execute malicious content by planting malicious [JavaScript](https://attack.mitre.org/techniques/T1059/007) within Electron applications.(Citation: Electron Security)


### Tactic
- [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/tactics/Defense Evasion]] (TA0005)

### Platforms
- macOS
- Windows
- Linux

### Permissions Required

### Mitigations

| ID | Name | Description |
| --- | --- | --- |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Execution Prevention\|M1038]] | Execution Prevention | Where possible, enforce binary and application integrity with digital signature verification to prevent untrusted code from executing. For example, do not use `shell.openExternal` with untrusted content.<br /><br />Where possible, set `nodeIntegration` to false, which disables access to the Node.js function.(Citation: Electron Security 3) By disabling access to the Node.js function, this may limit the ability to execute malicious commands by injecting JavaScript code.<br /><br />Do not disable `webSecurity`, which may allow for users of the application to invoke malicious content from online sources. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Exploit Protection\|M1050]] | Exploit Protection | Microsoft's Enhanced Mitigation Experience Toolkit (EMET) Attack Surface Reduction (ASR) feature can be used to block methods of using trusted binaries to bypass application control. <br />Ensure that Electron is updated to the latest version and critical vulnerabilities (such as nodeIntegration bypasses) are patched and cannot be exploited. |
| [[CyberSecurity/Security+/1-Threats-Attacks-Vulnerabilities/Attacking-Frameworks/MITRE ATT&CK/ICS-Attack/mitigations/Disable or Remove Feature or Program\|M1042]] | Disable or Remove Feature or Program | Remove or deny access to unnecessary and potentially vulnerable software and features to prevent abuse by adversaries. Many native binaries may not be necessary within a given environment: for example, consider disabling the Node.js integration in all renderers that display remote content to protect users by limiting adversaries’ power to plant malicious JavaScript within Electron applications.(Citation: Electron Security 2) |


---
### References

- mitre-attack: https://attack.mitre.org/techniques/T1218/015
- Electron 3: https://www.kaspersky.com/blog/electron-framework-security-issues/49035/
- Electron Security: https://www.electronjs.org/docs/latest/tutorial/using-native-node-modules
- Electron 6-8: https://medium.com/@MalFuzzer/one-electron-to-rule-them-all-dc2e9b263daf
- Electron 1: https://www.mend.io/blog/theres-a-new-stealer-variant-in-town-and-its-using-electron-to-stay-fully-undetected/
- Electron 2: https://www.first.org/resources/papers/conf2023/FIRSTCON23-TLP-CLEAR-Horejsi-Abusing-Electron-Based-Applications-in-Targeted-Attacks.pdf
