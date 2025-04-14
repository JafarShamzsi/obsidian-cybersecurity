## Overview

The CIA Triad is the foundational model for information security that defines three key properties that all secure systems must maintain: Confidentiality, Integrity, and Availability.

## Key Points

- CIA stands for Confidentiality, Integrity, and Availability
- Also sometimes referred to as AIC to avoid confusion with the Central Intelligence Agency
- Forms the basis for most security policies and controls
- All security measures can be mapped to at least one of these three principles

## Components

### Confidentiality

- Information can only be read by people explicitly authorized to access it
- Protects against unauthorized disclosure of data
- Implemented through:
    - Encryption
    - Access controls
    - Authentication mechanisms
    - Data classification

### Integrity

- Data remains stored and transferred as intended
- Any modification is unauthorized unless explicitly permitted through proper channels
- Ensures data has not been tampered with
- Implemented through:
    - Hashing
    - Digital signatures
    - Version control
    - Checksums
    - Access controls

### Availability

- Information is readily accessible to authorized users when needed
- Systems function as expected when required
- Implemented through:
    - Redundancy
    - Backups
    - Disaster recovery plans
    - Load balancing
    - RAID configurations

## Extended Model: CIA+

Some security frameworks extend the CIA Triad with additional properties:

### Non-repudiation

- Ensures that a person cannot deny their actions
- Creates accountability and prevents individuals from falsely denying their involvement
- Implemented through:
    - Digital signatures
    - Audit logs
    - Timestamps
    - Biometric authentication

## Related Concepts

- [[Data Classification]]
- [[Access Control Models]]
- [[Encryption]]
- [[Risk Management]]
- [[Security Controls]]

## Security+ Exam Relevance

- Domain 2: Architecture and Design
- Domain 5: Governance, Risk, and Compliance
- Fundamental concept that appears throughout the exam
- Essential for understanding the purpose of security controls

## Examples

- **Confidentiality**: Encrypting sensitive customer data in a database
- **Integrity**: Using digital signatures to verify email authenticity
- **Availability**: Implementing redundant servers to ensure service uptime
- **Non-repudiation**: Using transaction logs in a banking system

## Additional Resources

- NIST Special Publication 800-12
- CompTIA Security+ Study Guide (SY0-601) - Chapter 1

#security-fundamentals #exam-essential #governance #CIA