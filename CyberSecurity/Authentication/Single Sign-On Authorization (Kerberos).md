Kerberos is a secure, ticket-based **authentication and authorization protocol** used to implement Single Sign-On (SSO) in enterprise environments. It allows a user (principal) to authenticate once and access multiple services within a trusted domain without re-entering credentials.

## Key Components

| Component       | Description |
|----------------|-------------|
| **Principal**   | The user or service requesting access. |
| **KDC**         | Key Distribution Center — includes the Authentication Service (AS) and Ticket Granting Service (TGS). |
| **TGT**         | Ticket Granting Ticket — issued by the AS to request service tickets from the TGS. |
| **TGS**         | Ticket Granting Service — issues service tickets upon validation of the TGT. |
| **Service Ticket** | Used by the client to access a specific application server. |
| **Application Server** | The target server the user wants to access. |
| **Authenticator** | A time-stamped token encrypted with the session key to prove identity and freshness. |
![[5363-1692974862866.png]]
## Workflow Overview

1. **Initial Authentication (AS Exchange)**
    - The user logs in and sends an authentication request to the **Authentication Service** (AS) within the KDC.
    - The AS responds with:
        - A **TGT** (Ticket Granting Ticket), encrypted with the KDC's secret.
        - A **TGS session key**, encrypted with the user's secret key (derived from their password).
    - The user decrypts the TGS session key using their password. The TGT remains encrypted and untouched.

2. **Requesting Access to a Service (TGS Exchange)**
    - To access a domain service, the client (principal) sends:
        - The **TGT**.
        - The **name of the target service** (SPN).
        - An **authenticator**, encrypted with the TGS session key, containing:
            - Client ID
            - Timestamp

    - The TGS decrypts:
        - The TGT using the KDC’s secret key.
        - The authenticator using the TGS session key from the TGT.
    - Verification checks:
        - Ticket validity period
        - Ticket reuse (replay protection)

    - The TGS responds with:
        - **Service session key** (encrypted with the TGS session key).
        - **Service ticket** (contains client info and session key, encrypted using the application server’s secret key).

3. **Accessing the Application Server**
    - The principal sends:
        - The **service ticket** (which it cannot decrypt).
        - An **authenticator**, encrypted with the service session key.

    - The application server performs:
        - Decryption of the service ticket to retrieve the service session key.
        - Decryption of the authenticator using the session key.
        - Verification of the timestamp and client ID.

4. **Mutual Authentication (Optional)**
    - The application server sends back:
        - The timestamp from the authenticator, encrypted using the service session key.
    - The client decrypts and verifies it matches its original value.
    - This ensures **mutual authentication**, confirming the server’s identity.

5. **Session Established**
    - If successful, the server authorizes access based on its ACL (Access Control List).
    - Secure communication can now occur using the service session key.

## Kerberos Packet Structure

### Ticket Granting Ticket (TGT)
- Encrypted with the KDC secret.
- Contains:
    - Principal name
    - Timestamp
    - TGS session key
    - Expiration

### Service Ticket
- Encrypted with the application server’s secret key.
- Contains:
    - Client name
    - Timestamp
    - Service session key
    - Network address
    - Group SIDs (in Windows)

## Security Mechanisms

- **Replay protection**: Authenticator contains a timestamp.
- **Mutual authentication**: Server authenticates back to client using the same session key.
- **Short ticket lifespans**: Limits window for replay attacks.
- **End-to-End encryption**: Session keys used to encrypt authenticators and communication.

## Advantages

- Centralized authentication management.
- Secure mutual authentication.
- No password sent over the network.
- Facilitates secure SSO within the domain.

## Disadvantages

- **Single Point of Failure**: The KDC is critical; if it fails, no authentication can proceed.
- **Clock Synchronization Required**: Kerberos relies on timestamp-based authentication.
- **Complex Setup**: Requires careful domain and service principal configuration.

## Mitigation for KDC Failure

- **Backup KDCs**:
    - In Active Directory environments, multiple domain controllers can serve as redundant KDCs.
    - These ensure availability and load balancing.

## Visual Flow Summary

```text
1. Principal -> KDC (TGS): Sends TGT + Authenticator + Target Server Name
2. KDC (TGS) -> Principal: Sends Service Ticket + Service Session Key
3. Principal -> App Server: Sends Service Ticket + Authenticator
4. App Server -> Principal: Sends Encrypted Timestamp (optional, mutual auth)
5. App Server grants access
```

## Real-World Example

In a Windows Active Directory domain:

- The **client** logs into Windows using a domain account.
    
- Windows uses Kerberos behind the scenes to authenticate and obtain TGT from the domain controller.
    
- When accessing resources (e.g., file shares, email), it uses service tickets issued by the TGS.
    
- No password is re-entered — **Single Sign-On** is achieved.
    

## References

- RFC 4120 - The Kerberos Network Authentication Service
    
- Microsoft Docs – [How Kerberos works](https://docs.microsoft.com/en-us/windows-server/security/kerberos/kerberos-authentication-overview)
    
- NIST SP 800-63B – Digital Identity Guidelines
