The [GitHub Link for BloodHound and SharpHound](https://github.com/BloodHoundAD/) utils are very useful in the AD enumeration for gathering informations about logged on users, and general data collection. `In order to perform succesful enumeration remember to download the right versions of the tools.` If we are using BloodHound v4.3.1 we must use the relative SharpHound v4.3.1, otherwise this will not work and the import of the audit.zip will be stuck at 0%. Under Collectors/SharpHound.ps1 we can find the correct version supported from the current BloodHound build.

#### [SharpHound](https://github.com/BloodHoundAD/SharpHound)

SharpHound is used for the data collection part.

We first import it with

```powershell
Import-Module .\SharpHound.ps1
```

And we run the script, saving information in a ZIP file for easy transfer in our

```powershell
Invoke-BloodHound -CollectionMethod All -OutputDirectory <PATH> -OutputPrefix "audit"
```

For a SMB enumeration we can list the shares and check if we can access them

```powershell
Find-DomainShare
```

If in the sares we find some old credentials, encrypted with AES-256 we can decrypt it in the kali machine with

```powershell
gpp-decrypt <CREDENTIALS>
```

#### [BloodHound](https://github.com/BloodHoundAD/BloodHound)

Is a useful graphical interface for printing the SharpHound retrieved data. It can print various information and make a diagram on what victim target first to gain AD Admin access. Here we can list users groups, sessions etc. The element displayed with the full SID are local object of the machines.

A useful RAW query to list all computer in a domain is the following

```
MATCH(m:Computer) RETURN m
```

To list all users

```
MATCH(m:User) RETURN m
```

Find active session for users and bind them to the computer

```
MATCH p = (c:Computer)-[:HasSession]->(m:User) RETURN p
```

Delete data from Neo4J

```
match (a) -[r] -> () delete a, r
match (a) delete a
```