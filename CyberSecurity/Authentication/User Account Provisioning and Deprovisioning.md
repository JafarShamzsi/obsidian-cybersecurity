
User account provisioning is a critical process in identity and access management (IAM) that ensures users are granted the minimum necessary access rights and resources required for their roles, based on organizational policies and regulatory frameworks. It involves establishing a validated digital identity, issuing credentials, assigning system entitlements, and managing lifecycle changes.

Improper provisioning and deprovisioning introduces serious security risks, including privilege escalation, insider threats, orphaned accounts, and violations of regulatory compliance (e.g., HIPAA, SOX, GDPR).

---

### Identity Proofing

**Definition**: Identity proofing establishes a verified digital identity before account creation. The goal is to ensure that the entity requesting access is legitimate and uniquely identifiable.

**Procedures**:

- **Document Validation**: 
    
    - Government-issued photo ID (passport, national ID, driver’s license)
        
    - Matching personally identifiable information (PII): name, DoB, address
        
- **Biometric Validation** (if applicable)
    
- **Background Screening** (based on role sensitivity):
    
    - Employment verification
        
    - Educational verification
        
    - Criminal record check
        
    - Financial background (for finance-related roles)
        

**Standards/Frameworks**:

- NIST SP 800-63A: Digital Identity Guidelines – Enrollment and Identity Proofing
    
- ISO/IEC 29115: Entity Authentication Assurance Framework
    

---

### Credential Issuance

**Definition**: The process of assigning authentication mechanisms to the verified identity.

**Types of Authenticators**:

- **Something You Know**: Passwords, PINs
    
- **Something You Have**: Smartcards, OTP tokens, cryptographic USB keys (e.g., FIDO2, PIV)
    
- **Something You Are**: Biometrics (fingerprint, iris scan)
    

**Security Controls**:

- Password policies: length ≥12, complexity, expiration, history
    
- MFA enforcement for all privileged and remote access accounts
    
- Use of TOTP/HOTP (RFC 6238/4226) or FIDO2-based authenticators
    
- Secure storage of credentials: passwords hashed with bcrypt/scrypt/PBKDF2
    

**Credential Issuance Systems**:

- Identity Providers (IdP): Azure AD, Okta, ForgeRock
    
- Public Key Infrastructure (PKI) for digital certificate issuance
    

---

### IT Asset Issuance

**Definition**: Allocation of physical and logical assets required to perform assigned duties.

**Typical Assets**:

- Endpoints: laptops, desktops, mobile devices
    
- Licensed software: productivity tools, custom applications
    
- Secure remote access tools: VPN clients, VDI instances
    

**Operational Controls**:

- Inventory tracking via Configuration Management Database (CMDB)
    
- Asset tagging and association with unique user ID
    
- Endpoint protection: MDM, EDR, disk encryption (e.g., BitLocker, FileVault)
    
- Installation policies: Application Allowlisting, GPO/SCCM enforcement
    

**Shadow IT Risk**:

- Enforce policies to prevent unauthorized acquisition of IT assets
    
- Monitor network for rogue/unmanaged devices using NAC (Network Access Control)
    

---

### Security Awareness and Policy Onboarding

**Objective**: Ensure users are informed of acceptable use policies, data handling procedures, and security obligations.

**Training Requirements**:

- Acceptable Use Policy (AUP)
    
- Information security and phishing awareness
    
- Data classification and handling
    
- Password hygiene and MFA usage
    
- Reporting procedures for suspected security incidents
    

**Implementation**:

- Onboarding LMS integration with HRMS
    
- Training completion must be logged and auditable
    
- Annual retraining and simulated phishing tests
    

**Standards Compliance**:

- NIST SP 800-53 AT-2
    
- ISO/IEC 27001:2013 A.7.2.2
    
- CIS Control 14: Security Awareness and Skills Training
    

---

### Permission Assignment

**Definition**: Granting the minimum set of access rights necessary to perform authorized job functions (Principle of Least Privilege).

**Access Control Models**:

- **RBAC** (Role-Based Access Control): Access granted based on predefined roles
    
- **ABAC** (Attribute-Based Access Control): Policies evaluate user/environmental attributes (e.g., department, time, location)
    
- **MAC** (Mandatory Access Control): Labels and clearance levels used for access decisions (e.g., military systems)
    

**Entitlement Management**:

- Maintain access matrix mapping roles to entitlements
    
- Centralized IAM solutions for dynamic assignment and auditing
    
- Separation of Duties (SoD) enforced for financial/administrative systems
    

**Privileged Account Controls**:

- Use PAM (Privileged Access Management) solutions to:
    
    - Vault and rotate credentials
        
    - Enforce just-in-time (JIT) elevation
        
    - Record and audit privileged session activity
        
- Apply tiered administrative model (e.g., Microsoft’s Tier 0/1/2 model)
    

---

### Deprovisioning

**Definition**: Controlled and auditable revocation of all access rights and assets when a user leaves the organization or changes role.

**Deprovisioning Workflow**:

1. **Trigger Event**: HR termination notice, contract expiration, project completion
    
2. **Immediate Actions**:
    
    - Disable all accounts (AD, IdP, SaaS apps)
        
    - Revoke VPN and remote access
        
    - Lock down email and file access
        
    - Reclaim physical devices
        
3. **Follow-up Actions**:
    
    - Remove from all security groups, roles, RBAC mappings
        
    - Transfer or archive owned files and mailboxes per retention policy
        
    - Delete or archive account after holding period
        

**Automation**:

- Identity Governance and Administration (IGA) platforms for deprovisioning workflows (e.g., SailPoint, Saviynt)
    
- API-based revocation for federated cloud applications (SCIM, SAML, OAuth2)
    

**Risk Mitigation**:

- Conduct periodic account reconciliation audits
    
- Monitor for ghost/orphaned accounts
    
- Implement emergency disablement procedures for high-risk terminations
    

---

### Logging, Monitoring, and Auditing

- All provisioning/deprovisioning actions must be logged in a tamper-evident system (e.g., SIEM)
    
- Critical events (admin account creation, privilege elevation) should trigger real-time alerts
    
- Perform regular access reviews (quarterly recommended) and certification processes
    

---

### Related Standards and References

- **NIST SP 800-53 Rev. 5** – Access Control (AC), Identification and Authentication (IA)
    
- **ISO/IEC 27001/27002** – Annex A.9: Access Control
    
- **CIS Controls v8** – Control 5: Account Management
    
- **NIST SP 800-63A/B/C** – Digital Identity Guidelines
    
- **OWASP** – Authentication and Access Control Cheat Sheets