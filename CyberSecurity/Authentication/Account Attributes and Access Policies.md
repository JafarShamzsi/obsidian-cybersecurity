User accounts are critical control points in enterprise access management systems. They encapsulate identity attributes, define entitlements, and serve as security principals that can be authenticated, authorized, audited, and managed.

---
![[148-1692974862548.png]]
### Account Structure

Each user account in a managed system (e.g., Active Directory, LDAP, IdP) consists of the following core elements:

#### 1. **Security Identifier (SID)**

- A **globally unique** and **immutable** identifier assigned by the domain controller or OS.
    
- Used internally by the OS and security subsystems to reference the user, regardless of username changes.
    
- Format (Windows): `S-1-5-21-<domain-identifier>-<user-rid>`
    

#### 2. **Username / Principal Name**

- Human-readable login name.
    
- Often represented in formats:
    
    - `sAMAccountName` (legacy Windows)
        
    - `userPrincipalName (UPN)` (e.g., `jdoe@example.com`)
        

#### 3. **Credentials**

- Mechanism for authenticating the user.
    
- Typically includes:
    
    - Password hash (e.g., NTLM hash)
        
    - MFA tokens (TOTP, FIDO2)
        
    - X.509 certificates (for smartcards)
        

---

### Account Profile Attributes

User accounts are often extended with a **profile object** that defines custom attributes and user-specific environment settings.

#### Common Identity Attributes:

- `displayName`: Full legal name
    
- `mail`: Corporate email
    
- `telephoneNumber`: Contact number
    
- `department`: Organizational unit or business function
    
- `title`: Job title
    
- `manager`: Distinguished name (DN) of supervisor
    

#### Profile Features:

- **Account Picture**: JPEG/PNG image used for GUI personalization (e.g., `thumbnailPhoto`)
    
- **Home Folder**:
    
    - Network-mapped drive (e.g., `\\fileserver\users\jdoe`)
        
    - Contains user-specific documents, application data, and configuration files
        
- **Application Settings**:
    
    - Stored in `%APPDATA%` or registry hive (`HKCU`) on Windows
        
    - Supports per-user configuration profiles across sessions
        

---

### Access Rights and Policies

Access control defines the scope of actions a user account can perform on local and networked systems. These controls are enforced via permissions and policies.

#### Permission Models:

- **Discretionary Access Control (DAC)**:
    
    - Object owner sets access permissions (e.g., NTFS ACLs)
        
- **Role-Based Access Control (RBAC)**:
    
    - Access granted based on assigned roles (e.g., Helpdesk, Developer)
        
- **Mandatory Access Control (MAC)**:
    
    - Access governed by system-enforced classification levels (e.g., SELinux)
        
- **Attribute-Based Access Control (ABAC)**:
    
    - Policies evaluate identity and environmental attributes (e.g., `department == HR`)
        

#### Resource Permissions:

- Files/Folders: Read, Write, Modify, Full Control
    
- Print queues: Print, Manage Documents
    
- Shared resources: Connect, Modify, Share
    
- Application services: Start/stop services, access APIs
    

#### Inheritance:

- Direct assignment: ACLs/ACEs set on the user account
    
- Indirect assignment: Via membership in **security groups**, **distribution groups**, or **role containers**
    

---

### Group Policy Objects (GPOs) and Access Enforcement

On Windows networks using **Active Directory (AD)**, access policies are configured via **Group Policy Objects (GPOs)**.

#### GPO Concepts:

- **Group Policy Object (GPO)**:
    
    - A collection of settings applied to users or computers within AD boundaries.
        
- **Scope of Application**:
    
    - Sites
        
    - Domains
        
    - Organizational Units (OUs)
        

#### GPO Capabilities:

- **Logon Rights**:
    
    - `Allow log on locally`
        
    - `Allow log on through Remote Desktop Services`
        
- **System Permissions**:
    
    - `Shut down the system`
        
    - `Install device drivers`
        
- **Security Options**:
    
    - `Account lockout threshold`
        
    - `Interactive logon: Message text for users`
        
- **Software Restrictions**:
    
    - AppLocker policies for application allowlisting/blocking
        

#### GPO Management Tools:

- **Group Policy Management Console (GPMC)**
    
- **Group Policy Management Editor (gpedit.msc)**
    
- **PowerShell Cmdlets** (e.g., `Get-GPO`, `Set-GPLink`, `New-GPO`, `Backup-GPO`)
    

---

### Security Considerations

- Enforce **principle of least privilege (PoLP)** through group membership and GPO scoping.
    
- Audit and review:
    
    - **Account attributes**: Ensure role and department alignment
        
    - **GPO links**: Prevent policy bloat and conflicting settings
        
- Protect administrative accounts using **tiered administration**, **admin approval mode**, and **Protected Users group**.
    

---

### Best Practices

- Use **naming conventions** for users and groups (e.g., `svc_<service>`, `adm_<role>`)
    
- Regularly **audit group memberships** and **access rights**
    
- Disable dormant accounts after a defined period (e.g., 30/60 days)
    
- Apply **fine-grained password policies (FGPP)** via Password Settings Objects (PSOs)
    
- Utilize **LDAP queries** or **PowerShell scripts** for attribute validation and bulk updates
    

---

### Related References

- **Microsoft Docs** – [Group Policy Overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/group-policy-overview)
    
- **NIST SP 800-53 Rev. 5** – AC-2 (Account Management), AC-6 (Least Privilege)
    
- **ISO/IEC 27001:2013** – A.9: Access Control
    
- **CIS Controls v8** – Control 5: Account Management