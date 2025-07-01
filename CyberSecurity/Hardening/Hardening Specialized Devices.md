Industrial control systems (ICS), including supervisory control and data acquisition (SCADA) systems, embedded systems, real-time operating systems (RTOS), and Internet of Things (IoT) devices, have been targeted for attack more frequently in recent years due to their vital role in controlling critical infrastructures.

General hardening strategies apply to these systems, including common controls such as regular system updates, disabling unnecessary services, limiting network access, using secure credentials, and using role-based access controls. Network-level security should also be implemented to protect them, such as firewalls, IDS/IPS, transport encryption protocols like TLS and SSH, regular security audits, and penetration tests to help identify and remediate vulnerabilities.

### Hardening ICS/SCADA

For ICS/SCADA systems, hardening involves strict network segmentation to isolate these systems from the wider network and robust authentication and authorization processes to limit system access strictly. ICS/SCADA is often used to control physical operations.

Ensuring protection from cyber and physical threats is more crucial because breaches can result in environmental disasters, power/gas/water utility failure, and loss of life. A unique control often used to protect ICS/SCADA is unidirectional gateways (or data diodes), which ensure that data only flows outward from these systems, protecting them from inbound attacks.

### Hardening Embedded and RTOS

Given their constrained resources, simple embedded systems and RTOS typically do not support traditional security measures. Ideally, security is designed into these systems from the start, considering aspects such as secure coding practices, minimal design (where the system has only the features it needs to perform its function), secure boot mechanisms, physical tamper-proofing, and comprehensive security testing.

The organization must select devices based on security capabilities and quality instead of focusing solely on usability features and cost. IoT devices present similar hardening challenges as those outlined previously but also include significant privacy issues. Ultimately, each type of device requires a carefully tailored approach to hardening.

Security standards and certifications play a significant role in the security and integrity of real-time operating systems (RTOS) and embedded systems by providing guidelines, best practices, and benchmarks for designing, implementing, and evaluating the security of these systems. Security standards define requirements, controls, and procedures relevant to RTOS and embedded systems and include "Common Criteria" (ISO/IEC 15408), IEC 62443, MISRA-C, and CERT Secure Coding Standards. Certifications demonstrate compliance with specific security standards, assure that a system or product meets preestablished security requirements, and include ISO 27001, IEC 61508, and others.

Security standards and certifications help establish a framework for assessing, implementing, and validating security controls in RTOS and embedded systems. They provide a common language and criteria for evaluating the security of these systems and provide confidence in their security capabilities.