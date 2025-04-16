We can use [Seatbelt](https://github.com/GhostPack/Seatbelt.git) and [WinPeas](https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS) and then investigate on the results. It is also useful to check PowerShell history and `Windows Event Viewer`. If the result for Windows doesn't display colors, add this REG value

```powershell
 REG ADD HKCU\Console /v VirtualTerminalLevel /t REG_DWORD /d 1 
```

## Important

Always check installed programs under `C:\Program Files(x86)` or under folders as `Downloads` or `Documents`. We can find exploitable programs (search the program name with searchsploit) or interesting files like KeyPass vaults or hashed credentials to be cracked. Additionally, if we find some non-standard executable program that requires some sort of credentials for it, just do a `strings fileame.exe` because the credentials may be hard coded into it.

### Content
1. [[Windows Privilege Escalation - Enumeration]]
2. [[Windows Privilege Escalation - Service Binary Hijacking]]
3. [[Windows Privilege Escalation - Service DLL Hijacking]]
4. [[Windows Privilege Escalation - Unquoted Service Paths]]
5. [[Windows Privilege Escalation - Scheduled Tasks]]
6. [[Windows Privilege Escalation - Windows Services]]
7. [[Windows Privilege Escalation - Exploits]]
8. [[Windows Privilege Escalation - SAM and SYSTEM]]
9. [[Windows Privilege Escalation - UAC Bypass]]
