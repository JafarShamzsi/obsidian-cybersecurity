[PowerSploit](https://powersploit.readthedocs.io/en/latest/Recon/) is a useful tool that can be used to perform automatic enumeration. It has to be loaded in the system with

```powershell
powershell -ep bypass
Import-Module .\PowerSploit.ps1
```

Domain enumeration

```powershell
Get-NetDomain
```

User enumeration

```powershell
Get-NetUser
```

Groups enumeration

```powershell
Get-NetGroup
```

Get Access Control Entries

```powershell
Get-ObjectAcl -Identity <USERNAME>
```

Convert SID to name

```powershell
Convert-SidToName S-1-5-21-1987370270-658905905-1781884369-1104
```

Filter Identities for GenericAll ACL

```powershell
Get-ObjectAcl -Identity "Management Department" | ? {$_.ActiveDirectoryRights -eq "GenericAll"} | select SecurityIdentifier,ActiveDirectoryRights
```

Get-ObjectAcl -Identity stephanie

Enumerate object in the domain, selecting the operating system

```powershell
Get-NetComputer | select operatingsystem
```

To enumerate the machines in the domain with Admin access for our user

```powershell
Find-LocalAdminAccess
```

We can confirm it via

```powershell
Get-NetSession -ComputerName <COMPUTER-NAME>
```

Enumerate Service Principal Names

```powershell
Get-NetUser -SPN | select samaccountname,serviceprincipalname
```

Or with a builtin tool

```powershell
setspn -L <SERVICE-NAME>
```