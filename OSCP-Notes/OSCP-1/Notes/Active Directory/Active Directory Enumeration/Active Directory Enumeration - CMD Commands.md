Active Directory stores information about objects on the network and makes this information easy for administrators and users to find and use. Active Directory uses a structured data store as the basis for a logical, hierarchical organization of directory information. List users in domain

```powershell
net user /domain
```

Enumerate user in domain

```powershell
net user <USER> /domain
```

List groups in domain

```powershell
net group /domain
```

Enumerate group in domain

```powershell
net group <GROUP> /domain
```