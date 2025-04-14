## Overview
Access control ensures that an information system meets the **CIA triad** (Confidentiality, Integrity, Availability) by governing how subjects interact with objects. It is commonly implemented through **Identity and Access Management (IAM)** systems.

## Key Concepts
- **Subjects**: Entities (people, devices, software, processes) that request access.
- **Objects**: Resources such as networks, servers, databases, apps, or files.
- **Rights & Permissions**: Define what a subject can do with an object.

### IAM (Identity and Access Management)
IAM consists of four main processes:
1. **Identification**  
   - Creating an account or ID that uniquely represents a subject.
   - Example: A user registers an account on a website.
   - Example: maybe there is a ID related to a user that is not repeated

1. **Authentication**  
   - Proving that a subject is who they claim to be.
   - Uses authentication factors (passwords, biometrics, tokens).
   - Example: A user logs in using a password.

3. **Authorization**  
   - Defining and enforcing access rights.
   - Models include:
     - **Discretionary Access Control (DAC)** – Object owners set permissions.
     - **Mandatory Access Control (MAC)** – System-enforced rules dictate access.
   - Example: A user can only access files they have permission for.

4. **Accounting (Auditing)**  
   - Tracking resource usage and detecting unauthorized access.
   - Example: Logs showing a user accessed a file at a specific time.

![[Pasted image 20250320214106.png]]
### AAA Framework
- **Authentication, Authorization, and Accounting (AAA)**: A security model used in networking and enterprise security.
- **IAM vs. AAA**: IAM focuses on identity management; AAA emphasizes security enforcement.

## Real-World Applications
### E-commerce Site Example:
- **Identification**: Verify customers are legitimate (matching billing/delivery address).
- **Authentication**: Ensure customers can access their accounts securely.
- **Authorization**: Restrict access based on rules (e.g., only valid payment methods).
- **Accounting**: Log all transactions to prevent fraud and ensure order accountability.

### System Example:
- A web server authenticates itself with an SSL certificate when users connect.
- Role-based access control (RBAC) ensures that only administrators can modify system settings.

## Exam Tips
- **Know the difference between identification, authentication, authorization, and accounting.**
- **Understand the various access control models (DAC, MAC, RBAC).**
- **AAA is commonly tested, especially in network security contexts.**
- **Be familiar with IAM components and how they apply to users and systems.**

## Related Topics
- [[2-Architecture-Design/Access Control Models]]
- [[3-Implementation/Multi-Factor Authentication]]
- [[4-Operations-Incident-Response/Security Logs and Auditing]]
- [[Glossary#AAA]]

## Practice Questions
1. Which of the following best describes authentication?  
   - A. Determining what actions a subject can perform  
   - B. Creating a unique identifier for a subject  
   - C. Verifying the identity of a subject  
   - D. Logging a subject's activities  
   - **Answer:** C. Authentication verifies identity.

2. What is an example of an accounting function in access control?  
   - A. Restricting access based on permissions  
   - B. Logging a user’s access and actions  
   - C. Granting permissions to a user  
   - D. Encrypting login credentials  
   - **Answer:** B. Accounting tracks and logs user activity.

3. Which access control model allows resource owners to set permissions?  
   - A. MAC  
   - B. DAC  
   - C. RBAC  
   - D. ABAC  
   - **Answer:** B. DAC allows owners to set permissions.

