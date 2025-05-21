## Overview

Single Sign-On (SSO) is an authentication architecture that enables users to authenticate once and gain access to multiple systems or services without re-entering credentials. This mechanism is widely used in enterprise environments to enhance usability and centralize access control while reducing password fatigue and associated risks.

## Kerberos Authentication Protocol

Kerberos is a centralized network authentication protocol designed to provide strong authentication for client/server applications through secret-key cryptography. It was developed at MIT and is the default authentication protocol used in Microsoft Active Directory (AD) environments.

![[9269-1692974862756.png]]

### Core Entities

- **Client (Principal):** The entity requesting access (e.g., user or service).
- **Key Distribution Center (KDC):** Trusted third party that issues tickets.
  - **Authentication Service (AS)**
  - **Ticket Granting Service (TGS)**
- **Application Server (Service):** The endpoint that verifies the service ticket before granting access.

### Authentication Workflow

#### Step 1: Authentication Request to AS

The client initiates authentication by sending a request to the Authentication Service (AS) for a Ticket Granting Ticket (TGT).

- The request is encrypted with a hash of the user’s password.
- Contains:
  - Principal identifier
  - Timestamp (to prevent replay attacks)

The password hash is not transmitted across the network.

#### Step 2: AS Response

Upon validating the request, the AS issues:

- **Ticket Granting Ticket (TGT):**
  - Contains client identifier, IP address, timestamp, and expiration.
  - Encrypted using the KDC's secret key.
- **TGS Session Key:**
  - Used for secure communication between the client and TGS.
  - Encrypted using the user's password hash.

The TGT acts as a token that proves the client's identity. It does not authorize access to services directly.

#### Step 3: Requesting a Service Ticket

The client presents the TGT and an authenticator (encrypted using the TGS session key) to the TGS, requesting access to a specific application server.

#### Step 4: TGS Response

The TGS issues a **Service Ticket**, which is:

- Encrypted using the application server’s secret key.
- Contains the client's identity and session information.

The client uses this Service Ticket to authenticate directly with the target application server.

#### Step 5: Access to Application Server

The client presents the Service Ticket and a new authenticator to the application server. If validated, the server grants access.

### Ticket Summary

| Ticket Type        | Description                                                |
|--------------------|------------------------------------------------------------|
| Ticket Granting Ticket (TGT) | Proves identity to the TGS; issued by the AS |
| Service Ticket      | Grants access to a specific service; issued by the TGS     |

## Security Features

- **Mutual Authentication:** Both the client and the server verify each other’s identities.
- **Replay Protection:** Timestamps and session keys ensure tickets cannot be reused maliciously.
- **No Password Transmission:** Only password-derived keys are used in encrypted ticket exchanges.
- **Short-Lived Tickets:** Tickets are time-limited, reducing the attack surface in case of compromise.

## Use Case: Active Directory Authentication

In a Windows domain environment:

1. User logs into a domain-joined workstation.
2. The client authenticates to the domain controller (KDC) using Kerberos.
3. A TGT is issued, and subsequent service requests are handled via the TGS.
4. The user gains access to file shares, print services, and intranet applications without repeated logins.

## Integration

Kerberos is often used in conjunction with:

- **LDAP:** For directory-based authentication (e.g., AD).
- **Group Policy:** For access control policies.
- **Smart Cards or MFA:** As an alternative to password-based authentication.
- **Network Time Protocol (NTP):** Required for timestamp validation across systems.

## Comparison with Other SSO Mechanisms

| Feature               | Kerberos      | NTLM        | SAML        | OAuth 2.0 / OIDC     |
|----------------------|---------------|-------------|-------------|-----------------------|
| Authentication Type  | Symmetric Key | Challenge-Response | Assertion-based | Token-based          |
| Password Over Network| No            | Partially   | No          | No                    |
| Replay Protection    | Yes           | Limited     | Yes         | Yes                   |
| Mutual Authentication| Yes           | No          | Optional    | Optional              |
| Primary Use Case     | Enterprise / AD| Legacy Windows | Web SSO     | API / Web Applications|

## Protocol Dependencies

- **UDP/TCP 88:** Used by the KDC for Kerberos communications.
- **Time Synchronization:** Critical; systems must be synchronized to within 5 minutes (default) for tickets to be valid.

## References

- [RFC 4120 - The Kerberos Network Authentication Service (V5)](https://www.rfc-editor.org/rfc/rfc4120)
- Microsoft Docs – Kerberos Authentication Overview: https://learn.microsoft.com/en-us/windows-server/security/kerberos/kerberos-authentication-overview
- MIT Kerberos Documentation: https://web.mit.edu/kerberos/

