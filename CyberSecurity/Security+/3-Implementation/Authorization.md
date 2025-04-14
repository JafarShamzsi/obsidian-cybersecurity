# Authorization in Cybersecurity

## Overview  
**Authorization** is the process of **granting or restricting access** to resources based on a subject’s identity and permissions. It ensures that only **authorized users, systems, or processes** can access specific resources, preventing unauthorized actions. Authorization follows **identification and authentication** in the AAA model (**Authentication, Authorization, and Accounting**).  

## Key Concepts  

### **1. How Authorization Works**  
- A user or system **identifies** itself (e.g., by entering a username).  
- The system **authenticates** the subject (e.g., by verifying a password or biometric).  
- The system then **authorizes** the subject, determining what they can access and do.  

Example:  
- An **employee logs into a corporate system** (Identification & Authentication).  
- The system checks **their role and permissions** (Authorization).  
- The employee can **read reports but not modify them** (Access Control).  

### **2. Authorization Models**  

| **Model** | **Description** | **Example Use Case** |
|-----------|---------------|----------------------|
| **Discretionary Access Control (DAC)** | Owners of resources define who can access them. | A file owner grants read/write permissions to specific users. |
| **Mandatory Access Control (MAC)** | System-wide policies enforce access levels based on classification labels. | Military or government systems where access is based on clearance levels. |
| **Role-Based Access Control (RBAC)** | Access is assigned based on job roles. | A "Manager" role gets financial report access, but an "Employee" role does not. |
| **Attribute-Based Access Control (ABAC)** | Access is granted based on attributes (user, environment, actions). | Users can only access files from a company network during work hours. |
| **Rule-Based Access Control (RBAC)** | Rules determine access permissions. | A firewall blocks all traffic except from whitelisted IPs. |

### **3. Access Control Mechanisms**  
- **Permissions & Privileges** → Read, Write, Execute, Delete  
- **Access Control Lists (ACLs)** → Lists specifying which users or groups can access an object  
- **Group Policies** → Centralized security settings applied to users/groups in enterprise environments  
- **Least Privilege Principle** → Users get only the permissions they need for their role  

## Real-World Applications  
1. **Cloud Security** → Cloud providers use **RBAC & ABAC** for multi-tenant security.  
2. **Database Security** → Users are authorized to **query data but not alter schemas**.  
3. **Web Applications** → Authentication tokens authorize **API requests** for different user levels.  
4. **Enterprise Networks** → Employees have different permissions based on **Active Directory group policies**.  

## Exam Tips  
- **Authorization comes after authentication** (Identification → Authentication → Authorization).  
- **RBAC is the most common model used in enterprises.**  
- **MAC is stricter and often used in government/military environments.**  
- **ABAC is flexible and used for dynamic access control based on multiple attributes.**  
- **Least Privilege and Separation of Duties (SoD) reduce security risks.**  

## Related Topics  
- [[3-Implementation/Authentication Methods]]  
- [[3-Implementation/Access Control Models]]  
- [[4-Operations-Incident-Response/Logging and Monitoring]]  
- [[Glossary#Authorization]]  

## Practice Questions  
1. **Which of the following best describes authorization in cybersecurity?**  
   - A. Verifying a user's identity before granting access  
   - B. Granting or restricting access to resources based on permissions  
   - C. Logging user activities for forensic purposes  
   - D. Encrypting sensitive data to protect it from unauthorized access  
   - **Answer:** B. Granting or restricting access to resources based on permissions.  

2. **Which access control model assigns permissions based on job roles?**  
   - A. MAC  
   - B. DAC  
   - C. RBAC  
   - D. ABAC  
   - **Answer:** C. RBAC (Role-Based Access Control).  

3. **Which access control model enforces security labels and classification levels?**  
   - A. RBAC  
   - B. MAC  
   - C. DAC  
   - D. ABAC  
   - **Answer:** B. MAC (Mandatory Access Control).  



---
