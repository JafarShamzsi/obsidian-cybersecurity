The **Shared Responsibility Model (SRM)** defines the delineation of security responsibilities between a **Cloud Service Provider (CSP)** and a **cloud customer**. While the CSP is accountable for securing the **cloud infrastructure**, the customer is responsible for securing **what they put into** the cloud and **how they configure** cloud services.

> **Key Principle**: Risk is not transferred when adopting cloud services — it is shared. Security oversight must adapt accordingly.

---

##  Why the Shared Responsibility Model Matters

Failure to understand the SRM leads to misconfigurations, data leaks, and increased exposure to attacks. Misaligned assumptions between provider and customer can result in unpatched systems, poor access control, or lack of logging and monitoring.

Security is a **joint operation** that requires clearly defined controls at every service layer.

---

##  Core Areas of Responsibility

### Cloud Service Provider (CSP)

Responsible for securing the **underlying infrastructure**, including:

- **Physical security** of datacenters
    
- **Compute, storage, and networking infrastructure**
    
- **Foundational networking layers** (e.g., DDoS mitigation, firewalls)
    
- **Hypervisor and virtualization layers**
    
- **Tenant resource isolation and segregation**
    
- **Infrastructure-level identity and access controls**
    
- **Incident detection and response** for infrastructure-level events
    
- **Backups and redundancy** of hosted cloud services
    

### Cloud Customer

Responsible for securing **everything they control and configure**, including:

- **Identity and access management (IAM)** for users and services
    
- **Data classification, encryption, and key management**
    
- **Application-level security configurations**
    
- **Operating system hardening** (when applicable)
    
- **Network access rules and routing configurations**
    
- **Data residency and compliance enforcement**
    
- **User behavior monitoring and endpoint protection**
    

---

##  Service Models and Varying Responsibilities

The extent of customer responsibility **varies based on the service model**:

| Layer                                      | On-Premises | IaaS     | PaaS     | SaaS     | FaaS     |
| ------------------------------------------ | ----------- | -------- | -------- | -------- | -------- |
| Physical Security                          | Customer    | CSP      | CSP      | CSP      | CSP      |
| Infrastructure (Compute, Storage, Network) | Customer    | CSP      | CSP      | CSP      | CSP      |
| Host OS                                    | Customer    | Shared   | CSP      | CSP      | CSP      |
| Network Controls                           | Customer    | Shared   | CSP      | CSP      | CSP      |
| Application Logic                          | Customer    | Customer | Shared   | CSP      | Shared   |
| Data                                       | Customer    | Customer | Customer | Customer | Customer |
| IAM & User Controls                        | Customer    | Customer | Shared   | Shared   | Shared   |
> **FaaS (Function as a Service)**: A serverless model where developers deploy individual functions in response to events. The CSP manages infrastructure scaling, while customers manage code, data flow, and access controls.
![[6389-1692974866520.png]]
---

##  Responsibility Matrix (Detailed Table)

|Responsibility|On-Prem|IaaS|PaaS|SaaS|FaaS|CIS Controls Guide|CIS Foundations Benchmarks|
|---|---|---|---|---|---|---|---|
|Data Classification & Accountability|Customer|Customer|Customer|Customer|Customer|Yes|Yes|
|Client & Endpoint Protection|Customer|Customer|Customer|Shared|Shared|Yes|Yes|
|Identity & Access Management|Customer|Customer|Shared|Shared|Shared|Yes|Yes|
|Application-Level Controls|Customer|Customer|Shared|Shared|Shared|Yes|Yes|
|Network Controls|Customer|Shared|CSP|CSP|CSP|Yes|Yes|
|Host Infrastructure|Customer|Shared|CSP|CSP|CSP|Yes|No|
|Physical Security|Customer|CSP|CSP|CSP|CSP|No|No|
> **Note**: “Shared” implies a joint responsibility where both customer and CSP must implement, monitor, or validate controls.

---

##  Function-as-a-Service (FaaS) and Serverless Security

With **serverless computing**, application code runs in isolated function containers managed entirely by the CSP. Although customers benefit from elasticity and scalability, they must secure:

- **Function logic**
    
- **Input validation and error handling**
    
- **IAM roles for each function**
    
- **Secrets management and environmental variables**
    
- **API Gateways and trigger-based access control**
    

FaaS simplifies infrastructure but **reduces visibility** and **increases dependency** on CSP’s runtime security guarantees. Serverless functions must be treated as isolated microservices with proper boundaries.

---

##  Operational Considerations

### Logging and Monitoring

- Customers must enable **cloud-native logging solutions** (e.g., AWS CloudTrail, Azure Monitor).
    
- Use centralized **SIEM** to correlate events across cloud and on-prem assets.
    

### Patch Management

- For IaaS, customers must patch **guest OS** and **application layers**.
    
- In SaaS, patching is handled by the CSP, but **customer misconfigurations** can still lead to data exposure.
    

### Incident Response

- Develop **incident response playbooks** that align with cloud-specific events.
    
- Ensure **log retention and access** support forensic investigations.
    

### Configuration Management

- Employ **Infrastructure-as-Code (IaC)** with security validation (e.g., Terraform with Sentinel).
    
- Use **CSPM tools** to detect drift and misconfigurations across services.
    

---

##  Cloud Security Misconceptions

|Misconception|Reality|
|---|---|
|"The cloud provider handles all security."|Only for services they control (e.g., host OS, physical hardware). Customers must secure access, applications, and data.|
|"SaaS apps are secure by default."|Customers still configure access rights, sharing policies, and data retention.|
|"Shared responsibility is static."|It evolves with service type, deployment model, and compliance needs.|