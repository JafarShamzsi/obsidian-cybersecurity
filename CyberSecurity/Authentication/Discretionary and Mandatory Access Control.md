# Access Control Models

## Overview

**Access control models** define the frameworks through which authenticated users are granted permissions to access resources on networks, computers, and data systems. These models establish the principles for how security policies are implemented and enforced.

## Discretionary Access Control (DAC)

### Core Principles

![[DAC Principles]]

- **Owner-centric model** - resource owners determine access rights
- **Flexibility-focused** - prioritizes ease of use and customizability
- **Decentralized administration** - each resource owner makes independent decisions
- **Permission inheritance** - rights can be passed along to other users

### Implementation Mechanisms

- **Access Control Lists (ACLs)** - attached to each resource, listing users and their permissions
- **Capability tables** - attached to each user, listing resources they can access
- **Permission attributes** - read, write, execute, modify, delete, etc.

### Technical Operation

1. Resource creation establishes ownership
2. Owner receives full control over the resource by default
3. Owner can modify the ACL to grant specific rights to:
    - Individual users
    - User groups
    - Special identities (Everyone, Authenticated Users, etc.)
4. Rights can be inherited by:
    - Child objects (folders/files)
    - Processes running under user context

### Common Implementations

- **Windows NTFS file system**
    - Object ownership
    - Customizable permissions
    - Group Policy integration
- **UNIX/Linux file permissions**
    - Owner/group/world model
    - Read/write/execute permissions
    - Extended attributes
- **Database management systems**
    - Table/view ownership
    - GRANT/REVOKE privileges

### Strengths

- **High flexibility** - easily customizable to organizational needs
- **User autonomy** - empowers users to control their resources
- **Familiar model** - widely implemented and understood
- **Reduced administrative overhead** - distributed decision-making

### Weaknesses

![[DAC Weaknesses]]

- **Security policy fragmentation** - difficult to implement consistent policies
- **Vulnerable to [[Privilege Escalation|privilege escalation]]** - permissions can be transferred
- **Insider threat vulnerability** - legitimate users can make poor security decisions
- **[[Malware]] propagation risk** - malware inherits user's permissions
- **Compromised account exploitation** - attackers gain all permissions of compromised users
- **Limited security guarantees** - no formal verification of security properties

## Mandatory Access Control (MAC)

### Core Principles

![[MAC Principles]]

- **Rule-based model** - system enforces predetermined security policies
- **Centralized administration** - security administrators define all access rules
- **Security labels** - classification of all subjects and objects
- **Nondiscretionary enforcement** - users cannot modify security settings

### Implementation Mechanisms

- **Object classification labels** - security levels assigned to data/resources
    - Examples: Unclassified, Confidential, Secret, Top Secret
- **Subject clearance levels** - security levels assigned to users
- **Compartmentalization** - lateral segregation of data by category
    - Examples: HR, Finance, R&D, Marketing
- **Rule enforcement** - system manages all access decisions based on labels

### Multi-Level Security (MLS) Principles

- **Bell-LaPadula Model** (Confidentiality focus)
    - **Simple Security Property** - No read up (subjects cannot read objects at higher classification)
    - **Star Property** - No write down (subjects cannot write to objects at lower classification)
    - Prevents data leakage from higher to lower security classifications
- **Biba Model** (Integrity focus)
    - **Simple Integrity Property** - No read down (subjects cannot read lower integrity objects)
    - **Star Integrity Property** - No write up (subjects cannot write to higher integrity objects)
    - Prevents corruption of high-integrity data

### Common Implementations

- **SELinux** (Security-Enhanced Linux)
    - Type Enforcement
    - Role-Based Access Control
    - Multi-Level Security
- **TrustedSolaris**
    - Labeled file systems
    - Trusted path execution
- **Military/Government systems**
    - Classified information handling
    - Compartmentalized access

### Compartment-Based Access

![[MAC Compartments]]

- **Extends basic classification system**
- **Lateral security boundaries**
- **Need-to-know principle implementation**
- **Example scenario**:
    - Document: Secret classification + HR compartment
    - User needs: Secret clearance + HR compartment access
    - Even users with Top Secret clearance cannot access without HR compartment authorization

### Strengths

- **Strong security guarantees** - formal verification possible
- **Consistent policy enforcement** - system-wide rules
- **Defense against malware** - limits damage potential
- **Protection against insider threats** - users cannot override controls
- **Data leakage prevention** - controls information flow between security domains

### Weaknesses

- **Administrative overhead** - complex setup and maintenance
- **Reduced flexibility** - difficult to handle exceptions
- **User friction** - can impede legitimate work
- **Implementation complexity** - requires specialized expertise
- **Performance impact** - additional security checks affect system speed

## Comparison Table

|Characteristic|Discretionary Access Control|Mandatory Access Control|
|---|---|---|
|**Control Authority**|Resource owners|System/Security administrators|
|**Policy Determination**|Individual owners|Centralized policy|
|**Flexibility**|High|Low|
|**Security Strength**|Lower|Higher|
|**Administration**|Decentralized|Centralized|
|**Complexity**|Lower|Higher|
|**User Autonomy**|High|Low|
|**Policy Consistency**|Difficult to maintain|Consistent|
|**Implementation Cost**|Lower|Higher|
|**Common Use Cases**|General computing, workstations|Military, government, high-security environments|

## Implementation Considerations

### Hybrid Approaches

![[Hybrid Access Control]]

- **Role-Based Access Control (RBAC)** elements
    - Assigning permissions to roles rather than individuals
    - Users inherit permissions from assigned roles
- **Rule-Based Access Control** elements
    - Dynamic permission assignment based on conditions
    - Time-of-day, location, system state factors
- **MAC foundations with DAC flexibility**
    - Baseline mandatory policies
    - Discretionary adjustments within constraints

### Security Evaluation

- **Common Criteria** requirements
- **Assurance levels** for different implementations
- **Formal verification** of security properties

### Organizational Factors

- **Security requirements** vs. operational needs
- **Administrative resources** available
- **User security awareness** and training
- **Compliance requirements** (regulatory, contractual)

## Real-World Applications

### Defense/Intelligence

- **Classified information handling**
- **Compartmentalized access**
- **Strict MAC implementation**

### Corporate Environments

- **DAC for general resources**
- **Limited MAC for sensitive data**
- **Hybrid models for specific departments**

### Healthcare

- **Patient data protection**
- **Role-based access with MAC elements**
- **Audit and compliance requirements**

## Best Practices

### For DAC Environments

- **Regular permission audits**
- **Group-based permission management**
- **Principle of least privilege**
- **Default-deny policies**

### For MAC Environments

- **Clear classification guidelines**
- **Regular clearance reviews**
- **Compartment justification process**
- **Exception handling procedures**

## Related Concepts

### [[Access Control List]]

- Structure for storing subject/object permissions
- Implementation details in various systems

### [[Role-Based Access Control]]

- Permission assignment via roles
- Relationship to DAC and MAC

### [[Rule-Based Access Control]]

- Dynamic condition-based permissions
- Environmental and contextual factors

### [[Attribute-Based Access Control]]

- Advanced model using subject/object attributes
- Policy evaluation engines

## References

- NIST Special Publication 800-53: Security and Privacy Controls
- Orange Book (DoD Trusted Computer System Evaluation Criteria)
- Bell-LaPadula and Biba formal security models