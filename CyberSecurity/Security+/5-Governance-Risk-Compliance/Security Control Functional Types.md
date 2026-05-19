## Overview
Security controls can be classified based on **how they function** to protect systems and data. These functions help organizations enforce security policies, detect threats, and mitigate risks effectively.

## Primary Functional Types

### **1. Preventive Controls**
- **Goal**: Stop an attack before it happens.
- **How it works**: Eliminates or reduces the likelihood of an attack succeeding.
- **Examples**:
  - Firewalls with Access Control Lists (ACLs)
  - Antimalware software blocking threats
  - Intrusion Prevention Systems (IPS)
  - Security patches preventing exploits

### **2. Detective Controls**
- **Goal**: Identify and log suspicious activity during an attack.
- **How it works**: Detects security breaches but does not prevent them.
- **Examples**:
  - Security logs and monitoring tools
  - Intrusion Detection Systems (IDS)
  - Security Information and Event Management (SIEM)
  - Video surveillance recordings

### **3. Corrective Controls**
- **Goal**: Restore normal operations after a security incident.
- **How it works**: Reduces the impact of an attack and fixes vulnerabilities.
- **Examples**:
  - Data backups for recovery after ransomware attacks
  - Incident response plans
  - Patch management to fix vulnerabilities
  - System restores after malware infection

![[Pasted image 20250323190725.png]]

## Additional Functional Types

### **4. Directive Controls**
- **Goal**: Establish security policies and enforce compliance.
- **How it works**: Defines rules, best practices, and employee responsibilities.
- **Examples**:
  - Security policies and procedures
  - Standard Operating Procedures (SOPs)
  - Employee contracts with security clauses
  - Security awareness training

### **5. Deterrent Controls**
- **Goal**: Discourage attackers psychologically from attempting an intrusion.
- **How it works**: Warns potential attackers of consequences.
- **Examples**:
  - "This area is under surveillance" warning signs
  - Legal penalties for unauthorized access
  - Visible security guards at entry points

### **6. Compensating Controls**
- **Goal**: Provide an alternative control when a primary control is not feasible.
- **How it works**: Offers a different method to achieve the same level of security.
- **Examples**:
  - Using a VPN instead of direct encryption for secure data transmission
  - Implementing two-factor authentication (2FA) when password policies are weak
  - Using endpoint detection tools when traditional antivirus is ineffective

## Exam Tips
- **Preventive**: Stops attacks before they happen.
- **Detective**: Identifies and records ongoing attacks.
- **Corrective**: Mitigates damage and restores operations.
- **Directive**: Defines rules and best practices.
- **Deterrent**: Warns and discourages attackers.
- **Compensating**: Provides an alternative security method.

## Related Topics
- [[5-Governance-Risk-Compliance/Security Control Categories]]
- [[3-Implementation/Access Control Models]]
- [[Glossary#Security Control Functional Types]]

## Practice Questions
1. Which security control type focuses on preventing security incidents before they occur?  
   - A. Detective  
   - B. Preventive  
   - C. Corrective  
   - D. Directive  
   - **Answer**: B. Preventive

2. What type of security control is a warning sign stating, "Surveillance Cameras in Use"?  
   - A. Detective  
   - B. Corrective  
   - C. Deterrent  
   - D. Compensating  
   - **Answer**: C. Deterrent

3. Which control type helps an organization recover from an attack?  
   - A. Preventive  
   - B. Detective  
   - C. Corrective  
   - D. Directive  
   - **Answer**: C. Corrective