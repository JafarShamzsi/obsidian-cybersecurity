# Directory Services

A **directory service** is a centralized system used to store, organize, and manage identity-related data such as users, computers, groups, and network resources. It enables administrators to manage access control and network organization efficiently. Modern directory services are typically based on the **Lightweight Directory Access Protocol (LDAP)**, which is a standardized protocol derived from X.500.

## Core Components

### Objects
Directory services store data in the form of **objects**. An object represents a single entity and is an instance of an object class. Each object consists of multiple **attributes**.

Examples of object classes:
- `user`
- `group`
- `computer`
- `organizationalUnit`
- `printer`

### Attributes
Each object has attributes, which are key-value pairs that describe its properties.

Common attributes:
- `cn` (Common Name)
- `uid` (User ID)
- `mail` (Email address)
- `sAMAccountName` (Security Account Manager name in Windows)
- `memberOf` (Group membership)

## Directory Schema

A **directory schema** defines:
- The allowed object classes.
- The permitted attributes for each class.
- The format and data types of those attributes.
- Whether attributes are required (`MUST`) or optional (`MAY`).

Custom schemas can be created but should be used cautiously to ensure compatibility across different systems.

![[2586-1692974862656.png]]

## Distinguished Name (DN)

A **Distinguished Name (DN)** uniquely identifies an object within the directory hierarchy. It is constructed from a sequence of **attribute-value pairs**, listed from most specific to most general.

### DN Format
``` json
<Attribute>=<Value>,<Attribute>=<Value> 
```

### Example 
```json
CN=bobby,CN=users,DC=classroom,DC=local
```


This represents:
- Common Name: bobby
- Located in container: users
- Within domain: classroom.local

### Common DN Attributes

| Attribute | Description                              |
|-----------|------------------------------------------|
| CN        | Common Name                              |
| OU        | Organizational Unit                      |
| O         | Organization                             |
| C         | Country (ISO 3166-1 Alpha-2 code)        |
| DC        | Domain Component (e.g., parts of domain) |

### Relative Distinguished Name (RDN)

An **RDN** is the leftmost part of a DN and identifies the object uniquely within its immediate parent context.

In the example:  
`CN=bobby` is the RDN in  
`CN=bobby,CN=users,DC=classroom,DC=local`

## LDAP and X.500

LDAP (Lightweight Directory Access Protocol) is a protocol used to access and maintain distributed directory information services over a network. LDAP is based on the X.500 standard but is optimized for TCP/IP networks.

LDAP provides:
- Query and search operations
- Entry addition, deletion, and modification
- Schema definitions
- Directory tree navigation

LDAP directories are organized hierarchically, similar to a file system, with **containers**, **organizational units (OUs)**, and **entries**.

## Microsoft Active Directory (AD)

**Active Directory (AD)** is Microsoft’s LDAP-compatible directory service used for managing users, groups, and devices within a Windows domain environment. It uses Kerberos for authentication and supports features like Group Policy, domain trust, and replication.

### ADSI Edit

**ADSI Edit** is a GUI tool for low-level editing of Active Directory entries. It shows:
- Object names and classes
- Full Distinguished Names
- Attribute lists
- Hierarchical view of the directory

Example entry in ADSI Edit:

``` markdown
Name: bobby
Class: user
DN:  CN=bobby,CN=users,DC=classroom,DC=local
```


## Example Distinguished Name

A web server named `WIDGETWEB` in the marketing department of Widget Corporation, UK:

```
CN=WIDGETWEB,OU=Marketing,O=Widget,C=UK,DC=widget,DC=foo
```


Breakdown:
- CN=WIDGETWEB → object is the web server
- OU=Marketing → organizational unit
- O=Widget → organization
- C=UK → country
- DC=widget,DC=foo → domain `widget.foo`

## Practical Uses of Directory Services

- **Authentication:** Centralized login via LDAP or Active Directory
- **Authorization:** Group-based access control using directory group memberships
- **Policy Enforcement:** GPO (Group Policy Objects) in AD for enforcing security settings
- **Asset Management:** Track users, devices, printers, and services
- **Federated Identity:** Integrate with SSO, SAML, OpenID Connect for cross-platform authentication

## Security Considerations

- **Access Control Lists (ACLs):** Restrict who can view or modify directory entries
- **Encrypted Transport:** Use LDAPS (LDAP over SSL/TLS) to prevent credential theft
- **Audit Logging:** Monitor directory modifications and authentication attempts
- **Schema Protection:** Limit schema changes to prevent directory corruption

## Tools

- `ldapsearch`, `ldapadd`, `ldapmodify`: command-line tools to query and modify LDAP directories
- **ADSI Edit**: GUI editor for Windows Active Directory
- **Apache Directory Studio**: Cross-platform LDAP browser

## References

- RFC 4511 – Lightweight Directory Access Protocol (LDAP): The Protocol
- Microsoft Docs – Active Directory Schema Overview: https://docs.microsoft.com/en-us/windows/win32/adschema/active-directory-schema
- OpenLDAP Documentation – https://www.openldap.org/doc/
