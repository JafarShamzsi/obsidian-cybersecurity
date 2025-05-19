## Core Principles

**Least privilege** is a fundamental security principle that involves granting principals (users, processes, or systems) only the minimum permissions necessary to perform authorized tasks. This principle limits the potential damage from security incidents by constraining what an attacker can do with a compromised account or system.

![[Least Privilege Definition]]

> "The principle of least privilege requires that a subject be given no more privilege than necessary to perform a job." — NIST Special Publication 800-179

## Conceptual Framework

### Key Components

- **Necessity-based permissions** - only what's required to complete authorized work
- **Minimal scope of rights** - limiting breadth of accessible resources
- **Time-bound privileges** - ephemeral elevated permissions when needed
- **Contextual authorization** - permissions activated in appropriate circumstances
- **Continual reassessment** - regular privilege review and adjustment

### Security Benefits

- **Reduced attack surface** - minimizing potential exploitation points
- **Limited breach impact** - containing damage from compromised accounts
- **Malware containment** - restricting malicious software propagation
- **Lateral movement prevention** - impeding attacker progression through networks
- **Simplified forensics** - clearer audit trails for security investigations

## Implementation Process

### Design Phase

![[Least Privilege Design Phase]]

1. **Business workflow analysis**
    
    - Document authorized job functions and tasks
    - Identify required systems and resources
    - Determine minimal access levels needed
2. **Role engineering**
    
    - Create standardized role definitions
    - Map permissions to business functions
    - Establish role hierarchies and relationships
3. **Access policy development**
    
    - Document formal access requirements
    - Define approval workflows
    - Establish temporary access procedures

### Deployment Phase

1. **Permission mapping**
    
    - Translate business requirements to technical permissions
    - Configure access control mechanisms
    - Document permission assignments
2. **Default deny posture**
    
    - Configure systems to deny access by default
    - Explicitly enable only necessary permissions
    - Remove unnecessary default access rights
3. **Separation of duties**
    
    - Divide critical functions among multiple users
    - Prevent conflict of interest scenarios
    - Reduce fraud opportunities

### Operational Phase

1. **Privilege escalation procedures**
    
    - Establish processes for temporary privilege elevation
    - Implement time-bound access mechanisms
    - Create approval workflows for elevated rights
2. **Just-in-time (JIT) access**
    
    - Grant elevated permissions only when needed
    - Automatically revoke after task completion or timeout
    - Log all temporary privilege usage
3. **Break-glass procedures**
    
    - Emergency access protocols for critical systems
    - Heavily audited override mechanisms
    - Post-incident review requirements

## Technical Implementation

### Windows Environments

- **Fine-grained permissions**
    - NTFS file system ACLs
    - Registry permissions
    - Active Directory object permissions
- **User Rights Assignment**
    - Local security policy
    - Group Policy Objects (GPOs)
- **Privileged Access Management**
    - Just-in-time administration
    - Privileged Identity Management (PIM)

### Linux/Unix Environments

- **Traditional permission model**
    - User/group/world permissions
    - SUID/SGID/sticky bits
- **Access Control Lists**
    - Extended attributes
    - Fine-grained control
- **Capability-based security**
    - Linux capabilities
    - Dropping unnecessary privileges

### Database Systems

- **Role-based security models**
    - Database roles and permissions
    - Schema-level access control
- **Row and column level security**
    - Data-dependent access controls
    - Dynamic security policies

### Cloud Environments

- **IAM policies**
    - Resource-specific permissions
    - Policy conditions and constraints
- **Service accounts**
    - Purpose-specific identities
    - Managed service identities
- **Resource boundaries**
    - Virtual network isolation
    - Resource group permissions

## Implementation Challenges

### Technical Challenges

![[Least Privilege Technical Challenges]]

- **Permission complexity**
    - Diverse access control mechanisms
    - Interdependent permission systems
    - Technical expertise requirements
- **Legacy system limitations**
    - Coarse permission granularity
    - Lack of auditability
    - Monolithic permission structures
- **Effective permission analysis**
    - Calculating cumulative permissions
    - Identifying indirect access paths
    - Permission inheritance complications

### Operational Challenges

- **Performance vs. security balance**
    - Too restrictive = productivity impact
    - Too permissive = security risks
- **Administrative overhead**
    - Regular permission reviews
    - User access recertification
    - Change management processes
- **Exception handling**
    - Temporary access needs
    - Emergency access provisions
    - Legitimate edge cases

### Organizational Challenges

- **Business resistance**
    - User convenience expectations
    - Deadline pressures undermining security
    - "But it's always worked this way" mentality
- **Knowledge gaps**
    - Understanding business requirements
    - Technical implementation details
    - Security implications
- **Resource constraints**
    - Time limitations
    - Budget restrictions
    - Personnel shortages

## Authorization Creep

![[Authorization Creep]] **Authorization creep** (also called privilege creep or permission creep) describes the gradual accumulation of access rights beyond what is necessary for a user's current role or responsibilities.

### Common Causes

- **Role transitions**
    - Users changing job functions without permission adjustments
    - Retaining old permissions after promotion or transfer
- **Short-term projects**
    - Temporary permissions that are never revoked
    - Project-based access outliving its purpose
- **Administrative convenience**
    - Granting excessive permissions to avoid future requests
    - Copying permissions from other users without analysis
- **Shadow permissions**
    - Indirect access through group memberships
    - Inherited permissions from parent objects

### Detection Methods

- **User access reviews**
    - Regular certification of access rights
    - Manager approval of current permissions
- **Automated analysis**
    - Permission comparison against role baselines
    - Identifying outliers and anomalies
- **Access utilization monitoring**
    - Tracking actual resource usage patterns
    - Flagging unused permissions

### Remediation Approaches

- **Regular permission pruning**
    - Removing unnecessary access rights
    - Cleaning up group memberships
- **Access recertification campaigns**
    - Periodic formal review of all permissions
    - Attestation by managers and system owners
- **Automated time-based controls**
    - Expiration dates for elevated privileges
    - Scheduled permission reviews

## Continuous Monitoring and Auditing

### Auditing Components

- **Permission change tracking**
    - Logging all access control modifications
    - Recording who changed what permissions and when
- **Access attempt logging**
    - Successful and failed access attempts
    - Privilege escalation events
- **Administrative action monitoring**
    - Security group membership changes
    - Account creation and modification

### Tools and Techniques

![[Effective Permissions Analysis]]

- **Effective permissions calculators**
    - Analyzing cumulative access rights
    - Accounting for inheritance and group memberships
- **Permission comparison tools**
    - Identifying deviations from baseline
    - Detecting unauthorized changes
- **Access certification platforms**
    - Streamlining review processes
    - Automating recertification workflows

### Metrics and Reporting

- **Privilege distribution statistics**
    - Users with administrative rights
    - Permission density analysis
- **Compliance metrics**
    - Segregation of duties violations
    - Unauthorized access attempts
- **Trend analysis**
    - Permission growth over time
    - Access request patterns

## Least Privilege in Special Contexts

### Administrative Accounts

- **Tiered administration model**
    - Separate administrative tiers
    - Limited privilege scope for each tier
- **Just enough administration**
    - Task-specific administrative roles
    - Limited duration of elevated rights
- **Administrative workstation isolation**
    - Hardened systems for administrative tasks
    - Network isolation for privileged operations

### Service Accounts

- **Purpose-specific accounts**
    - Dedicated to single applications/services
    - Minimized permissions for required functions
- **Managed service identities**
    - Automatically rotated credentials
    - Tightly scoped permissions
- **Group Managed Service Accounts**
    - Automated password management
    - Domain-based service identities

### Developer Environments

- **Development vs. production separation**
    - Reduced privileges in production
    - Sandbox environments for testing
- **CI/CD pipeline security**
    - Least privilege build agents
    - Separated deployment permissions
- **Code execution boundaries**
    - Application sandboxing
    - Container isolation

## Case Studies and Examples

### Healthcare Organization

- **Clinical staff access**
    - Role-based permissions
    - Patient relationship-based access
    - Emergency override protocols
- **Audit outcomes**
    - Reduced data exposure incidents
    - Improved regulatory compliance
    - Simplified investigation processes

### Financial Institution

- **Transaction authorization limits**
    - Graduated approval thresholds
    - Multi-party approval requirements
- **Implementation results**
    - Fraud reduction
    - Simplified compliance reporting
    - Enhanced security posture

## Best Practices

### Technical Controls

- **Use role-based access control**
    - Standardize permission assignments
    - Simplify management overhead
- **Implement time-bound permissions**
    - Auto-expiring elevated rights
    - Regular permission reviews
- **Leverage automated tools**
    - Permission analysis software
    - Access recertification platforms

### Process Controls

- **Document permission requirements**
    - Clear role definitions
    - Business justification for access
- **Establish formal review cycles**
    - Quarterly/annual recertification
    - Post-project permission cleanup
- **Create approval workflows**
    - Multi-level authorization for sensitive access
    - Risk-based approval routing

### Governance Controls

- **Develop comprehensive policies**
    - Least privilege requirements
    - User accountability
- **Establish metrics and reporting**
    - Permission distribution analysis
    - Privilege usage patterns
- **Conduct regular training**
    - Security awareness
    - Proper access request procedures

## Related Concepts

- [[Defense in Depth]]
- [[Separation of Duties]]
- [[Role-Based Access Control]]
- [[Zero Trust Security Model]]
- [[Privileged Access Management]]

## References and Standards

- NIST Special Publication 800-53: Security and Privacy Controls
- NIST Special Publication 800-171: Protecting Controlled Unclassified Information
- CIS Controls v8: Control 5 - Account Management
- ISO 27001: A.9 Access Control
- MITRE ATT&CK: Privilege Escalation Tactics