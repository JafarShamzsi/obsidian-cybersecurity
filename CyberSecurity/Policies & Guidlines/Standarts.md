Standards define the expected outcome of a task, such as a particular configuration state for a server, or performance baseline for a service. The selection and application of standards within an organization center on various dynamic elements such as regulatory requirements, business-specific needs, risk management strategies, industry practices, and stakeholder expectations.

Regulatory requirements are the primary driver for adopting standards. The unique operational differences between organizations dictate varying legal requirements and security, privacy, and data protection regulations. These requirements often require implementing specific standards or using guidelines for achieving compliance. The healthcare industry in the United States is a classic example, where providers must comply with stringent data protection and privacy standards established by the Health Insurance Portability and Accountability Act (HIPAA).

Depending on the nature of its operations, customer base, or technological dependencies, each organization must adopt standards that specifically address its needs. For example, organizations heavily utilizing credit card transactions will adopt the PCI DSS standard to safeguard the cardholder data environment (CDE). Similarly, cloud-reliant organizations often prefer adopting ISO/IEC 27017 and ISO/IEC 27018 to ensure safe and secure cloud operations.

Risk management strategies organizations stress the need for appropriate standards. Standards help identify, evaluate, and manage risks and fortify the organization's resilience against security incidents or data breaches. ISO/IEC 27001, for example, provides a comprehensive framework for an information security management system (ISMS) designed to aid organizations in effectively managing security risks. Adherence to industry best practices also influences the adoption of standards. Conforming to widely accepted and tested standards demonstrates an organization's commitment to upholding high security and data protection levels to bolster the organization's reputation and build trust with customers and partners. Stakeholder expectations (such as customers, partners, vendors, investors, executive boards, etc.) significantly influence the choice of standards too. Stakeholders view adherence to recognized standards as an affirmation of the organization's dedication to quality, security, and reliability.

The choice of standards should not be a procedural decision but instead a strategic one. The selection of standards involves a thoughtful balance of legal and regulatory requirements, business-specific needs, risk management protocols, industry best practices, and stakeholder expectations. Adopting standards impacts how a business operates, and selecting appropriate standards helps an organization run more effectively. In contrast, adopting the wrong standards, or failing to plan the implementation of standards properly, can have severe negative consequences.

### Industry Standards

Common industry standards used by public and private organizations include the following:

- **ISO/IEC 27001** —An international standard that provides an information security management system (ISMS) framework to ensure adequate and proportionate security controls are in place.
- **ISO/IEC 27002** —This is a companion standard to ISO 27001 and provides detailed guidance on specific controls to include in an ISMS.
- **ISO/IEC 27017** —An extension to ISO 27001 and specific to cloud services.
- **ISO/IEC 27018** —Another addition to ISO 27001, and specific to protecting personally identifiable information (PII) in public clouds.
- **NIST (National Institute of Standards and Technology) Special Publication 800-63** —A US government standard for digital identity guidelines, including password and access control requirements.
- **PCI DSS (Payment Card Industry Data Security Standard)** —A standard for organizations that handle credit cards from major card providers, including requirements for protecting cardholder data.
- **FIPS (Federal Information Processing Standards)** —FIPS are standards and guidelines developed by NIST for federal computer systems in the United States that specify requirements for cryptography.

Common industry standards such as these play a significant role in auditing by providing a benchmark for evaluating organizational compliance and security practices. Standards such as ISO 27001, NIST SP800-63, PCI DSS, and FIPS provide comprehensive details and requirements for information security, risk management, data protection, and privacy. Auditing against these standards helps organizations assess their adherence to best practices, identify gaps or vulnerabilities, and demonstrate their commitment to maintaining a secure and compliant environment.

### Internal Standards

Organizations also establish internal standards to ensure the safety and integrity of operations and protect valuable resources such as data, intellectual property, and hardware. Internal standards provide consistent descriptions to define and manage important organizational practices. Standards differ from policies in a few ways. A simplistic view of the differences between the two is that standards focus on implementation, whereas policies focus on business practices.

Password standards describe the specific technical requirements required to design and implement systems, including how passwords are managed within those systems to ensure that different systems can interoperate and use consistent password-handling methods.

- **Hashing Algorithms** —Defines requirements for the hash functions used to store passwords.
- **Password Salting** —Defines the methods used to protect password hashes to protect them from rainbow table attacks.
- **Secure Password Transmission** —Defines the methods for secure password transmission, including details regarding appropriate cipher suites.
- **Password Reset** —Defines appropriate identity verification methods to protect password reset requests from exploitation.
- **Password Managers** —Defines the requirements for password managers that organizations may choose to incorporate.

Access control standards ensure that only authorized individuals can access the systems and data they need to do their jobs to protect sensitive information and help prevent accidental changes or damage. Internally developed access control standards typically include the following elements:

- **Access Control Models** —Defines appropriate access models for different use cases. Examples include role-based access control (RBAC), discretionary access control (DAC), and mandatory access control (MAC), among others.
- **User Identity Verification** —Defines acceptable methods to verify identities before granting access. Examples include simple passwords, security tokens, biometric data, and other methods.
- **Privilege Management** —Defines the methods for managing user privileges to ensure they have the minimum required access.
- **Authentication Protocols** —Defines specific acceptable authentication protocols, such as Kerberos, OAuth, or SAML.
- **Session Management** —Defines allowable session management practices, including requirements for session timeouts, secure generation and transmission of session cookies, and other similar requirements.
- **Audit Trails** —Defines mandatory audit capabilities designed to assist with identifying and investigating security incidents.

Physical security standards protect data centers, computer rooms, wiring closets, cabling, hardware, and infrastructure comprising the IT environment and the people who use and maintain them. Some examples include the following :

- **Building Security** —Methods for securing facilities, including card access systems, CCTV surveillance, and security personnel.
- **Workstation Security** —Standards for physically securing laptops or other portable devices.
- **Datacenter and Server Room Security** —Defines requirements for card access, biometric scans, sign-in/sign-out logs, and escorted access for visitors.
- **Equipment Disposal** —Defines requirements for securely disposing (or repurposing) equipment to ensure that sensitive data is irrecoverable.
- **Visitor Management** —Defines the requirements for managing visitors, such as sign-in/sign-out procedures, visitor badges, and escorted access requirements.

Encryption protects data from unauthorized access, and it is vital for securing data both at rest (stored data) and in transit (data being transmitted). Encryption standards identify the acceptable cipher suites and expected procedures needed to provide assurance that data remains protected.

- **Encryption Algorithms** —Defines allowable encryption algorithms, such as AES (Advanced Encryption Standard) for symmetric or ECC for asymmetric encryption.
- **Key Length** —Defines the minimum allowable key lengths for different types of encryption.
- **Key Management** —Defines how keys are generated, distributed, stored, and changed. It often includes requirements for using secure key management systems, procedures for regularly changing keys, and procedures for revoking them if they are compromised.