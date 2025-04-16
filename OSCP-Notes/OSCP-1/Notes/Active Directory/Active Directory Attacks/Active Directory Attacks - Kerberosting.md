With kerberoasting we are requesting SPN's TGS to the DC. The user that can access the service, for the Windows AD design, can access also the SPN and then the TGS, in order to use the service. We will abuse a service ticket in order to crack the password of the service account. We can run the attack from Rubeus with a user in the AD, and will be targeted only the **Service Principal Names** linked to the account user.

From the Kali machine we can run the attack with

```shell
sudo impacket-GetUserSPNs -request -dc-ip <DC-IP> corp.com/<USER>
```

The `-request` flag is requesting the DC a TGS for every SPN the logged user has access to. Dumping the tickets could let us to the password because it contains password of the SPN in hash. The TGS ticket will begin with this format: `$krb5tgs$23$`.

From the Windows machine we can use Rubeus

```powershell
.\Rubeus.exe kerberoast /outfile:hashes.kerberoast
```

Again now we copy the hash and we crack it with hashcat with the Kerberos code

```shell
sudo hashcat -m 13100 hashes.kerberoast /usr/share/wordlists/rockyou.txt --force
```
