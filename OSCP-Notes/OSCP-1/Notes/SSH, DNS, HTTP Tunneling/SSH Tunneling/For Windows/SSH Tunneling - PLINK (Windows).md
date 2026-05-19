Plink is the CLI version of PuTTY that allow us to use SSH Remote Forwarding if the OpenSSH service is missing. The syntax specifies the LOCAL-PORT on which Kali will listen and the REMOTE-PORT the Windows Machine will forward the connection to. This is useful in scenarios in which we have access only through CLI on the Windows Machine 1 and we want to connect via RDP to the Windows Machine 2, reachable only from the first Windows Machine.

```

KALI ---SSH--- WINDOWS-1 ---RDP--- WINDOWS-2
 |________________RDP__________________|

```

A simple plink Remote Forwarding is the following

```powershell
C:\Windows\Temp\plink.exe -ssh -l kali -pw <YOUR PASSWORD HERE> -R 127.0.0.1:<LOCAL-PORT>:127.0.0.1:<REMOTE-PORT> <KALI-IP>
```