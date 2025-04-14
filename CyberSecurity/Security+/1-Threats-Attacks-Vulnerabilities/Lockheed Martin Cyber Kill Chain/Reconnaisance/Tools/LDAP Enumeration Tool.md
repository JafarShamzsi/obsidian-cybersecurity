## Overview

LDAP (Lightweight Directory Access Protocol) enumeration tools are used to query, explore, and extract information from directory services like Active Directory. These tools are essential for both system administrators managing directory services and security professionals performing penetration tests or security assessments.

## Popular LDAP Enumeration Tools

### 1. Ldapsearch

#### Overview

Ldapsearch is a command-line utility included in the OpenLDAP suite that allows users to search LDAP directories using a simple, yet powerful syntax.

#### Installation

**On Debian/Ubuntu:**

```bash
apt-get install ldap-utils
```

**On RHEL/CentOS:**

```bash
yum install openldap-clients
```

**On macOS:**

```bash
brew install openldap
```

#### Basic Usage

```bash
ldapsearch -x -h <hostname> -p <port> -b "dc=example,dc=com" -D "cn=admin,dc=example,dc=com" -w "password" "(objectClass=*)"
```

#### Common Parameters

- `-x`: Use simple authentication
- `-h`: LDAP server hostname
- `-p`: LDAP server port (default: 389, or 636 for LDAPS)
- `-b`: Search base (starting point for the search)
- `-D`: Bind DN (Distinguished Name) for authentication
- `-w`: Password for authentication
- `-Z`: Use StartTLS for secure connection
- `-H`: URI format (ldap://hostname:port)

#### Practical Examples

**Anonymous bind and search:**

```bash
ldapsearch -x -h ldap.example.com -b "dc=example,dc=com" "(objectClass=*)"
```

**Search for all users:**

```bash
ldapsearch -x -h ldap.example.com -b "dc=example,dc=com" "(objectClass=user)"
```

**Search for a specific user:**

```bash
ldapsearch -x -h ldap.example.com -b "dc=example,dc=com" "(sAMAccountName=jsmith)"
```

**Output only specific attributes:**

```bash
ldapsearch -x -h ldap.example.com -b "dc=example,dc=com" "(objectClass=user)" sAMAccountName mail telephoneNumber
```

#### Troubleshooting

- **Connection refused**: Verify hostname, port, and firewall settings
- **Invalid credentials**: Check the bind DN and password
- **No results**: Verify the search base and filter
- **TLS error**: Check certificate validity and TLS configuration

### 2. ADExplorer (Sysinternals)

#### Overview

ADExplorer is a GUI-based Active Directory viewer and editor from Microsoft's Sysinternals suite. It allows for browsing and modification of Active Directory databases.

#### Installation

1. Download from the [Microsoft Sysinternals website](https://docs.microsoft.com/en-us/sysinternals/downloads/adexplorer)
2. No installation required; run the executable directly

#### Basic Usage

1. Launch ADExplorer.exe
2. Connect to a domain by entering the domain controller address
3. Provide authentication credentials when prompted
4. Browse the AD structure through the GUI interface

#### Key Features

- Tree view of AD structure
- Advanced search capabilities
- Snapshot feature for comparing directory changes over time
- Property editor for modifying attributes
- Favorites feature for quick access to commonly used objects

#### Practical Uses

- Quickly browse AD structure without writing LDAP queries
- Take snapshots before and after changes to verify implementations
- Export directory information to various formats
- Compare snapshots to identify unauthorized changes

#### Troubleshooting

- **Connection failure**: Verify domain controller name and credentials
- **Access denied**: Check user permissions in Active Directory
- **Slow performance**: Use filters to narrow search scope
- **Cannot modify attributes**: Verify user has write permissions

### 3. Bloodhound

#### Overview

Bloodhound is an advanced AD reconnaissance tool that uses graph theory to reveal hidden relationships and attack paths within Active Directory environments.

#### Installation

**Prerequisites:**

- Neo4j graph database
- Python (for SharpHound)

**Install Neo4j:**

```bash
# Download and install from https://neo4j.com/download/
```

**Install Bloodhound:**

```bash
# On Kali Linux
apt install bloodhound

# Alternative: download from GitHub
git clone https://github.com/BloodHoundAD/BloodHound.git
```

#### Basic Usage

1. Configure and start Neo4j database

```bash
neo4j console
```

2. Run SharpHound (data collector) in the target domain

```powershell
# Using PowerShell
Import-Module .\SharpHound.ps1
Invoke-BloodHound -CollectionMethod All
```

3. Launch Bloodhound and import the collected data

```bash
bloodhound
```

#### Key Features

- Visual mapping of AD relationships
- Pre-built queries for common attack paths
- Custom query support using Cypher query language
- Detailed information about users, groups, and computers
- Shortest path analysis to domain admin and other privileged accounts

#### Practical Examples

**Finding all domain admins:**

```cypher
MATCH (n:User)-[:MemberOf*1..]->(g:Group) WHERE g.name =~ "(?i)DOMAIN ADMINS@.*" RETURN n, g
```

**Finding kerberoastable users:**

```cypher
MATCH (n:User) WHERE n.hasspn=true RETURN n
```

**Identifying computers where specific users have logged in:**

```cypher
MATCH (u:User {name:"JSMITH@EXAMPLE.COM"})-[:HasSession]->(c:Computer) RETURN u,c
```

#### Troubleshooting

- **Neo4j connection issues**: Verify Neo4j is running and credentials are correct
- **No data appears**: Check SharpHound output for errors
- **Incomplete data**: Ensure appropriate collection methods were used
- **Performance issues**: Increase memory allocation for Neo4j

### 4. Enum4linux

#### Overview

Enum4linux is a tool for enumerating information from Windows and Samba systems. While primarily focused on SMB, it includes LDAP enumeration capabilities.

#### Installation

**On Kali Linux:**

```bash
# Already installed by default

# If needed:
apt-get install enum4linux
```

**From GitHub:**

```bash
git clone https://github.com/CiscoCXSecurity/enum4linux.git
cd enum4linux
chmod +x enum4linux.pl
```

#### Basic Usage

```bash
enum4linux -a <target_ip>
```

#### Common Parameters

- `-a`: All simple enumeration (recommended)
- `-u`: Username to use (default: "")
- `-p`: Password to use (default: "")
- `-U`: Get userlist
- `-G`: Get group list
- `-S`: Get sharelist
- `-P`: Get password policy information
- `-n`: Do an nmblookup (similar to nbtstat)

#### Practical Examples

**Complete enumeration:**

```bash
enum4linux -a 192.168.1.100
```

**User enumeration with credentials:**

```bash
enum4linux -u "administrator" -p "password" -U 192.168.1.100
```

**Group enumeration:**

```bash
enum4linux -G 192.168.1.100
```

#### Troubleshooting

- **SMB signing errors**: Use `-K` flag to skip SMB signing check
- **Connection refused**: Verify target is reachable and service is running
- **Access denied**: Check credentials or try anonymous access
- **No output**: Use verbose mode with `-v` flag

### 5. Impacket-GetADUsers

#### Overview

Part of the Impacket suite, GetADUsers.py is a Python script that retrieves users information from Active Directory.

#### Installation

```bash
# Install from pip
pip install impacket

# Alternative: install from source
git clone https://github.com/SecureAuthCorp/impacket.git
cd impacket
pip install .
```

#### Basic Usage

```bash
GetADUsers.py -all domain/username:password@domain_controller
```

#### Common Parameters

- `-all`: List all users in the domain
- `-dc-ip`: IP address of the domain controller
- `-user`: Specific user to query
- `-debug`: Turn on debugging output

#### Practical Examples

**List all users in a domain:**

```bash
GetADUsers.py -all -dc-ip 192.168.1.100 example.com/administrator:P@ssw0rd@192.168.1.100
```

**Get information about a specific user:**

```bash
GetADUsers.py -dc-ip 192.168.1.100 -user jsmith example.com/administrator:P@ssw0rd@192.168.1.100
```

#### Troubleshooting

- **Authentication failures**: Verify credentials and domain information
- **Connection issues**: Check network connectivity and firewall settings
- **Kerberos errors**: Ensure time synchronization between systems
- **Missing dependencies**: Install required Python packages

### 6. LDAPDomainDump

#### Overview

LDAPDomainDump is a Python tool that extracts and visualizes data from an LDAP server, particularly useful for Active Directory environments.

#### Installation

```bash
pip install ldapdomaindump

# Alternative: install from source
git clone https://github.com/dirkjanm/ldapdomaindump.git
cd ldapdomaindump
pip install .
```

#### Basic Usage

```bash
ldapdomaindump -u 'DOMAIN\username' -p 'password' ldap://domain_controller
```

#### Common Parameters

- `-u`: Username for authentication
- `-p`: Password for authentication
- `-d`: Base DN to use (default: auto-detect)
- `-o`: Output directory
- `--no-html`: Disable HTML output
- `--no-json`: Disable JSON output
- `--no-grep`: Disable greppable output

#### Practical Examples

**Dump entire domain with auto-detected basedn:**

```bash
ldapdomaindump -u 'EXAMPLE\administrator' -p 'P@ssw0rd' ldap://192.168.1.100
```

**Specify output directory:**

```bash
ldapdomaindump -u 'EXAMPLE\administrator' -p 'P@ssw0rd' -o output_folder ldap://192.168.1.100
```

**Use LDAPS (encrypted):**

```bash
ldapdomaindump -u 'EXAMPLE\administrator' -p 'P@ssw0rd' ldaps://192.168.1.100
```

#### Output Files

- **domain_users.html/.json/.grep**: All domain users
- **domain_groups.html/.json/.grep**: All domain groups
- **domain_computers.html/.json/.grep**: All domain computers
- **domain_policy.html/.json/.grep**: Domain policy information
- **domain_trusts.html/.json/.grep**: Domain trust relationships

#### Troubleshooting

- **Connection errors**: Verify server address and port
- **Authentication failures**: Check username and password format
- **Empty results**: Verify base DN is correct
- **SSL/TLS errors**: Check certificate validity or use `-n` to ignore certificate errors

### 7. windapsearch

#### Overview

windapsearch is a Python script specifically designed for enumerating users, groups, and computers from Windows domains through LDAP queries.

#### Installation

```bash
git clone https://github.com/ropnop/windapsearch.git
cd windapsearch
pip install -r requirements.txt
```

#### Basic Usage

```bash
python windapsearch.py -d example.com --dc-ip 192.168.1.100 -u 'username' -p 'password' --functionality
```

#### Common Parameters

- `-d`: Domain to search
- `--dc-ip`: Domain controller IP
- `-u`: Username
- `-p`: Password
- `-m`: Module to use (users, groups, computers, etc.)
- `--full`: Return all attributes
- `-o`: Output file path

#### Practical Examples

**Enumerate all users:**

```bash
python windapsearch.py -d example.com --dc-ip 192.168.1.100 -u 'username' -p 'password' -m users
```

**Find all users with the description containing "admin":**

```bash
python windapsearch.py -d example.com --dc-ip 192.168.1.100 -u 'username' -p 'password' -m custom --filter "(&(objectClass=user)(description=*admin*))"
```

**List all domain admins:**

```bash
python windapsearch.py -d example.com --dc-ip 192.168.1.100 -u 'username' -p 'password' -m domainadmins
```

**Custom LDAP query:**

```bash
python windapsearch.py -d example.com --dc-ip 192.168.1.100 -u 'username' -p 'password' -m custom --filter "(objectClass=user)" --attrs cn,description,memberOf
```

#### Troubleshooting

- **Authentication errors**: Verify domain, username, and password
- **Connection refused**: Check network connectivity and firewall settings
- **Invalid filter syntax**: Review custom LDAP filter syntax
- **Missing attributes**: Use `--full` flag to return all attributes

## Real-World Use Cases

### 1. Security Assessments

```
Scenario: Performing an authorized security assessment of an Active Directory environment
Tools: Bloodhound, LDAPDomainDump
Process:
1. Collect data using SharpHound or similar collector
2. Import data into Bloodhound
3. Analyze potential attack paths and excessive privileges
4. Document findings and recommendations
```

### 2. User Access Auditing

```
Scenario: Auditing user accounts for compliance purposes
Tools: Ldapsearch, windapsearch
Process:
1. Enumerate all user accounts
2. Filter for specific criteria (inactive, privileged, etc.)
3. Export results to CSV for documentation
4. Compare against authorized user lists
```

### 3. Active Directory Health Checks

```
Scenario: Regular health check of AD environment
Tools: ADExplorer, Ldapsearch
Process:
1. Take baseline snapshot using ADExplorer
2. Perform periodic snapshots
3. Compare snapshots to identify unauthorized changes
4. Verify security settings using targeted LDAP queries
```

### 4. Group Membership Verification

```
Scenario: Verifying group memberships for access control
Tools: windapsearch, LDAPDomainDump
Process:
1. Extract group membership information
2. Focus on privileged groups (Domain Admins, Enterprise Admins, etc.)
3. Cross-reference with approved access lists
4. Identify unauthorized group memberships
```

### 5. Unauthorized Service Account Discovery

```
Scenario: Finding service accounts with excessive privileges
Tools: Bloodhound, windapsearch
Process:
1. Enumerate service accounts using custom LDAP filters
2. Check for service accounts in privileged groups
3. Identify service accounts with concerning properties (non-expiring passwords, etc.)
4. Document findings for remediation
```

## Best Practices

### 1. Authentication and Authorization

- Use read-only accounts for enumeration when possible
- Create dedicated service accounts for authorized LDAP queries
- Use least privilege principles for enumeration accounts
- Consider using LDAPS (LDAP over SSL/TLS) for encrypted queries

### 2. Performance Considerations

- Narrow search scope with specific base DNs
- Use efficient filters to reduce result size
- Schedule intensive enumeration during off-hours
- Consider paging for large result sets

### 3. Security Precautions

- Log all LDAP enumeration activities
- Monitor for excessive or unusual LDAP queries
- Use rate limiting on LDAP servers
- Implement account lockout policies to prevent brute force
- Regularly audit enumeration tools and accounts

### 4. Results Handling

- Treat enumeration results as sensitive information
- Encrypt stored results
- Establish data retention policies for enumeration results
- Ensure proper access controls for reports and exports

## Advanced Techniques

### 1. Custom LDAP Filters

Crafting efficient LDAP filters is essential for precise enumeration:

**Find users with non-expiring passwords:**

```
(&(objectCategory=person)(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=65536))
```

**Find disabled accounts:**

```
(&(objectCategory=person)(objectClass=user)(userAccountControl:1.2.840.113556.1.4.803:=2))
```

**Find computers with specific operating system:**

```
(&(objectCategory=computer)(operatingSystem=*Windows Server 2019*))
```

**Find users who haven't logged in for 90 days:**

```
(&(objectCategory=person)(objectClass=user)(lastLogon<={90_days_ago_timestamp}))
```

### 2. Automated Enumeration Scripts

Example Python script using ldap3 library:

```python
#!/usr/bin/env python3
import ldap3
from ldap3 import Connection, Server, ALL, NTLM

def enumerate_users(server_ip, domain, username, password):
    # Create server object
    server = Server(server_ip, get_info=ALL)
    
    # Create connection object
    conn = Connection(
        server,
        user=f"{domain}\\{username}",
        password=password,
        authentication=NTLM
    )
    
    # Bind to the server
    if not conn.bind():
        print(f"Error connecting to LDAP server: {conn.result}")
        return
    
    # Search base
    base_dn = ",".join([f"DC={dc}" for dc in domain.split(".")])
    
    # Search filter
    search_filter = "(&(objectCategory=person)(objectClass=user))"
    
    # Attributes to retrieve
    attributes = ['sAMAccountName', 'mail', 'description', 'memberOf']
    
    # Perform the search
    conn.search(
        search_base=base_dn,
        search_filter=search_filter,
        attributes=attributes
    )
    
    # Process results
    users = []
    for entry in conn.entries:
        user_data = {
            'username': entry.sAMAccountName.value,
            'email': entry.mail.value if hasattr(entry, 'mail') else None,
            'description': entry.description.value if hasattr(entry, 'description') else None,
            'groups': [g.split(',')[0].replace('CN=', '') for g in entry.memberOf.values] if hasattr(entry, 'memberOf') else []
        }
        users.append(user_data)
    
    return users

# Example usage
if __name__ == "__main__":
    server_ip = "192.168.1.100"
    domain = "example.com"
    username = "enumerator"
    password = "SecureP@ssw0rd"
    
    users = enumerate_users(server_ip, domain, username, password)
    for user in users:
        print(f"Username: {user['username']}")
        print(f"Email: {user['email']}")
        print(f"Description: {user['description']}")
        print(f"Groups: {', '.join(user['groups'])}")
        print("-" * 40)
```

### 3. LDAP Query Optimization

- **Use indexed attributes**: sAMAccountName, objectGUID, objectSid are indexed by default
- **Limit returned attributes**: Only request needed attributes
- **Use paged results**: For large result sets
- **Combine filters efficiently**: Use AND (&) before OR (|) when possible

## Comparison of LDAP Enumeration Tools

|Tool|Interface|AD Focus|Authentication|Output Formats|Visualization|Platform|
|---|---|---|---|---|---|---|
|Ldapsearch|CLI|No|Simple, SASL|LDIF|No|Windows, Linux, macOS|
|ADExplorer|GUI|Yes|NTLM, Kerberos|Snapshots|Tree view|Windows|
|Bloodhound|GUI|Yes|N/A (imports data)|JSON|Graph|Windows, Linux, macOS|
|Enum4linux|CLI|Partial|Simple, NTLM|Text|No|Linux|
|Impacket-GetADUsers|CLI|Yes|NTLM, Kerberos|Text|No|Windows, Linux, macOS|
|LDAPDomainDump|CLI|Yes|Simple, NTLM|HTML, JSON, Grep|HTML tables|Windows, Linux, macOS|
|windapsearch|CLI|Yes|Simple, NTLM|Text, CSV|No|Windows, Linux, macOS|

## Defensive Measures Against Unauthorized LDAP Enumeration

### 1. LDAP Query Auditing

- Enable LDAP query logging on domain controllers
- Monitor for excessive or suspicious query patterns
- Set up alerts for enumeration tool signatures

### 2. Network-Level Protection

- Implement network segmentation to restrict LDAP access
- Use firewalls to limit LDAP traffic to authorized systems
- Monitor for unusual LDAP traffic patterns

### 3. Account Security

- Implement least privilege for directory service accounts
- Use read-only domain controllers where appropriate
- Configure account lockout policies to prevent brute force

### 4. LDAP Hardening

- Enable LDAP signing and channel binding
- Require LDAPS (LDAP over SSL/TLS) for all queries
- Disable anonymous LDAP binds
- Implement LDAP query rate limiting

## Resources

- [Microsoft Active Directory LDAP Documentation](https://docs.microsoft.com/en-us/openspecs/windows_protocols/ms-adts/d2435927-0999-4c62-8c6d-13ba31a52e1a)
- [LDAP Filter Syntax Reference](https://social.technet.microsoft.com/wiki/contents/articles/5392.active-directory-ldap-syntax-filters.aspx)
- [LDAP Security Best Practices](https://www.ietf.org/rfc/rfc2829.txt)
- [Bloodhound Documentation](https://bloodhound.readthedocs.io/)
- [OpenLDAP Documentation](https://www.openldap.org/doc/)