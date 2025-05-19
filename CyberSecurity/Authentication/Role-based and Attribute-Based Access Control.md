## Overview

Role-Based Access Control (RBAC) and Attribute-Based Access Control (ABAC) represent advanced access control models that provide more flexibility than traditional [[Mandatory Access Control]] while maintaining stronger security guarantees than [[Discretionary Access Control]]. These models implement nondiscretionary, rules-based permission assignments that align more closely with organizational structures and security requirements.

## Role-Based Access Control (RBAC)

### Core Principles

![[RBAC Principles]]

- **Task-oriented permissions** - rights defined by job functions rather than individuals
- **Role-based assignment** - users inherit permissions through role membership
- **Centralized administration** - system owners control role definitions
- **Nondiscretionary implementation** - users cannot modify permissions
- **Implicit rights acquisition** - permissions obtained through role association

### Implementation Components

- **Roles** - collections of permissions required for specific job functions
- **Subjects** - users or service accounts assigned to roles
- **Operations** - actions that can be performed on objects
- **Objects** - resources that can be accessed

### RBAC Models

1. **Flat RBAC**
    
    - Basic role assignment
    - Users assigned to roles
    - Roles assigned permissions
    - User-role assignment many-to-many
2. **Hierarchical RBAC**
    
    - Roles arranged in hierarchy
    - Permission inheritance through hierarchy
    - Senior roles inherit permissions from junior roles
    - Reflects organizational structure
3. **Constrained RBAC**
    
    - Adds separation of duties
    - Mutually exclusive roles
    - Numerical limitations on role assignments
    - Advanced security policy enforcement
4. **Symmetric RBAC**
    
    - Permission-role review capability
    - Determines permissions assigned to roles
    - Identifies roles with specific permissions
    - Aids in compliance auditing

### Implementation Through Security Groups

![[Security Groups vs Roles]]

- **Security groups** as role approximation
    - Users assigned to security groups
    - Permissions assigned to groups
    - Users inherit group permissions
- **Differences from pure RBAC**
    - Security group assignment typically discretionary
    - Permissions typically permanent rather than task-based
    - Limited constraints on administrator privilege escalation
    - ACL-based rather than true role enforcement

### RBAC in Different Environments

- **Windows Active Directory**
    - Built-in security groups
    - Custom security groups
    - Group Policy enforcement
- **Linux/Unix**
    - Traditional group permissions
    - sudo configuration
    - Pluggable Authentication Modules (PAM)
- **Cloud Environments**
    - AWS IAM roles
    - Azure RBAC
    - GCP IAM roles

### Strengths

- **Simplified administration** - reduced permission management complexity
- **Scalability** - easily adapts to organizational growth
- **Policy alignment** - maps to business functions
- **Reduced privilege creep** - easier to audit and adjust
- **Compliance support** - supports principle of least privilege

### Limitations

- **Coarse granularity** - may grant more permissions than strictly necessary
- **Static nature** - doesn't adapt to changing contexts
- **Implementation challenges** - defining optimal roles requires analysis
- **Role explosion** - proliferation of highly specific roles
- **Limited contextual awareness** - doesn't consider environmental factors

## Attribute-Based Access Control (ABAC)

### Core Principles

![[ABAC Principles]]

- **Policy-based decisions** - access determined by rules evaluating attributes
- **Fine-grained control** - highly specific access decisions
- **Dynamic evaluation** - contextual factors considered in real-time
- **Flexible implementation** - adaptable to complex organizations
- **Comprehensive security model** - considers multiple security dimensions

### Key Components

- **Subjects** - users or entities requesting access
    - Attributes: roles, clearance, department, location
- **Objects** - resources being accessed
    - Attributes: classification, owner, type, sensitivity
- **Actions** - operations performed on objects
    - Attributes: read, write, delete, approve
- **Environment** - contextual information
    - Attributes: time, location, security level, threat condition
- **Policies** - rules determining access decisions
    - Example: `IF (subject.clearance ≥ object.classification) AND (subject.department = object.department) AND (environment.time BETWEEN 9AM AND 5PM) THEN allow.access`

### Policy Enforcement Points

- **Policy Decision Point (PDP)** - evaluates access requests against policies
- **Policy Enforcement Point (PEP)** - implements access decisions
- **Policy Information Point (PIP)** - provides attribute information
- **Policy Administration Point (PAP)** - manages policies

### Implementation Mechanisms

- **XACML** (eXtensible Access Control Markup Language)
    - XML-based language for policies
    - Standardized request/response framework
    - Distributed policy enforcement
- **Custom policy engines**
    - Organization-specific rule sets
    - Integration with existing systems
    - Specialized security requirements

### Advanced Security Features

- **M-of-N Control**
    
    - Requires minimum number (M) of authorized agents from total pool (N)
    - Example: 3-of-5 administrators must approve privileged actions
    - Prevents single point of compromise
    - Common in high-security environments
- **Separation of Duties**
    
    - Divides critical functions among multiple users
    - Prevents conflict of interest
    - Reduces fraud opportunity
    - Example: Person approving payment cannot be same as requester
- **Context-Aware Security**
    
    - Time-based restrictions
    - Location-based access control
    - Device security posture assessment
    - Behavioral analysis and anomaly detection

### Real-World Applications

- **Healthcare**
    
    - Patient data access based on provider role, relationship, emergency status
    - Compliance with HIPAA requirements
    - Context-sensitive access to medical records
- **Financial Services**
    
    - Transaction approval based on amount, account type, user history
    - Fraud detection and prevention
    - Regulatory compliance enforcement
- **Government/Military**
    
    - Access based on clearance, compartment, need-to-know
    - Location and device security requirements
    - Enhanced security for classified information

### Strengths

- **Granular control** - precise access decisions
- **Contextual awareness** - adapts to changing conditions
- **Flexibility** - handles complex policy requirements
- **Reduced administrative overhead** - centralized policy management
- **Future-proof** - easily adapts to new requirements

### Limitations

- **Implementation complexity** - sophisticated rule sets required
- **Performance impact** - real-time policy evaluation
- **Attribute management** - maintaining accurate attribute information
- **Policy conflicts** - potential for contradictory rules
- **Visibility challenges** - understanding effective permissions

## Comparison: RBAC vs ABAC

|Characteristic|Role-Based Access Control|Attribute-Based Access Control|
|---|---|---|
|**Granularity**|Coarse (role-level)|Fine (attribute-level)|
|**Complexity**|Lower|Higher|
|**Administration**|Simpler|More complex|
|**Flexibility**|Limited|Extensive|
|**Context Awareness**|Minimal|Comprehensive|
|**Implementation Effort**|Moderate|High|
|**Performance Impact**|Lower|Higher|
|**Scalability**|Good for static environments|Better for dynamic environments|
|**Primary Use Case**|Well-defined organizational structures|Complex, context-dependent scenarios|

## Hybrid Approaches

![[Hybrid Access Control Models]]

- **RBAC with attribute constraints**
    - Role assignment based on attributes
    - Permission activation conditional on context
- **Attribute-enhanced RBAC**
    - Basic structure from RBAC
    - Fine-tuning with attributes
- **Risk-adaptive access control**
    - Dynamic risk assessment
    - Adaptive security posture

## Implementation Best Practices

### For RBAC

- **Role engineering** - methodical approach to role definition
- **Least privilege principle** - minimum necessary permissions
- **Regular role review** - prevent privilege creep
- **Role lifecycle management** - creation, modification, retirement
- **Temporary role assignment** - just-in-time access

### For ABAC

- **Policy framework development** - consistent rule structure
- **Attribute governance** - ensure accuracy and freshness
- **Performance optimization** - efficient rule evaluation
- **Policy testing and simulation** - verify expected behavior
- **Monitoring and auditing** - track policy effectiveness

## Migration Strategies

- **DAC to RBAC transition**
    - Group mapping
    - Permission analysis
    - Incremental implementation
- **RBAC to ABAC evolution**
    - Role attributes as starting point
    - Gradual context incorporation
    - Phased policy development

## Future Trends

- **AI-driven access control**
    - Machine learning for policy optimization
    - Behavioral analysis for anomaly detection
- **Zero Trust integration**
    - Continuous authentication and authorization
    - Device posture as critical attribute
- **Blockchain-based attribute verification**
    - Decentralized attribute storage
    - Immutable policy records

## Related Concepts

- [[Policy-Based Access Control]]
- [[Risk-Based Access Control]]
- [[Relationship-Based Access Control]]
- [[Zero Trust Security Model]]

## References

- NIST Special Publication 800-162: Guide to Attribute Based Access Control Definition and Considerations
- NIST Special Publication 800-207: Zero Trust Architecture
- OASIS XACML Standard
- Ferraiolo, D., Kuhn, D. R., & Chandramouli, R. (2007). Role-Based Access Control