## NTLM

Windows New Technology LAN Manager (NTLM) is a suite of security protocols offered by Microsoft to authenticate users’ identity and protect the integrity and confidentiality of their activity. At its core, NTLM is a single sign on (SSO) tool that relies on a challenge-response protocol to confirm the user without requiring them to submit a password. Despite known vulnerabilities, NTLM remains widely deployed even on new systems in order to maintain compatibility with legacy clients and servers. While NTLM is still supported by Microsoft, it has been replaced by Kerberos as the default authentication protocol in Windows 2000 and subsequent Active Directory (AD) domains.

```
- The user shares their username, password and domain name with the client.
- The client develops a scrambled version of the password — or hash — and deletes the full password.
- The client passes a plain text version of the username to the relevant server.
- The server replies to the client with a challenge, which is a 16-byte random number.
- In response, the client sends the challenge encrypted by the hash of the user’s password.
- The server then sends the challenge, response and username to the domain controller (DC).
- The DC retrieves the user’s password from the database and uses it to encrypt the challenge.
- The DC then compares the encrypted challenge and client response. If these two pieces match, then the user is authenticated and access is granted.
```


Visual Representation of NTLM

```
                      NTLM Authentication Process

   Client                  Server                          DC
  _______                _______                         _______
 |       |              |       |                       |       |
 |       |              |       |                       |       |
 |CLIENT |              |SERVER |                       |  DC   |
 |       |              |       |                       |       |
 |_______|              |_______|                       |_______|
     |                      |                               |
     |  NTLM_NEGOTIATE_MSG  |                               |
     |--------------------->|                               |
     |                      |                               |
     |                      |                               |
     |  NTLM_CHALLENGE_MSG  |                               |
     |<---------------------|                               |
     |                      |                               |
     |                      |                               |
     | NTLM_AUTHENTICATE_MSG|                               |
     |--------------------->|                               |
     |                      |                               |
     |                      | NETLOGON_NETWORK_INFO         |
     |                      |------------------------------>|
     |                      |                               |
     |                      | NETLOGON_VALIDATION_SAM_INFO4 |
     |                      |<------------------------------|
     |                      |                               |


```

## Kerberos

Kerberos authentication is currently the default authorization technology used by Microsoft Windows. It provides a credible security solution for businesses of all sizes. Kerberos uses symmetric key cryptography and a key distribution center (KDC) to authenticate and verify user identities. A KDC involves three aspects:

```
- A ticket-granting server (TGS) that connects the user with the service server (SS)
- A Kerberos database that stores the password and identification of all verified users 
- An authentication server (AS) that performs the initial authentication 
```

During authentication, Kerberos stores the specific ticket for each session on the end-user's device. Instead of a password, a Kerberos-aware service looks for this ticket. Kerberos authentication takes place in a Kerberos realm, an environment in which a KDC is authorized to authenticate a service, host, or user.

Kerberos authentication is a multi step process that consists of the following components:

```
- The client who initiates the need for a service request on the user's behalf 
- The server, which hosts the service that the user needs access to
- The AS, which performs client authentication. If authentication is successful, the client is issued a ticket-granting ticket (TGT) or user authentication token, which is proof that the client has been authenticated. 
- The KDC and its three components: the AS, the TGS, and the Kerberos database
- The TGS application that issues service tickets 
```

Visual Representation of Kerberos

```
                  Kerberos Authentication Process

    Kerberos Client    Domain Controller & KDC   Resource Server
   ________________     ______________________    _______________
  |                |   |                      |  |               |
  |  ____________  |   |   ________________   |  |   _________   |
  | |            | |   |  |                |  |  |  |         |  |
  | |  CLIENT    | |   |  |   DOMAIN       |  |  |  | RESOURCE|  |
  | |____________| |   |  | CONTROLLER &   |  |  |  | SERVER  |  |
  |________________|   |  |      KDC       |  |  |  |_________|  |
        __|__          |  |________________|  |  |               |
       /     \         |                      |  |               |
      /_______\        |______________________|  |_______________|

     |                                        |                |
     | 1. Request TGT with NTLM pass          |                |
     |--------------------------------------->|                |
     |                                        |                |
     | 1. Receive TGT                         |                |
     |<---------------------------------------|                |
     |                                        |                |
     | 2. Request Service Ticket with TGT     |                |
     |--------------------------------------->|                |
     |                                        |                |
     | 2. Receive Service Ticket              |                |
     |<---------------------------------------|                |
     |                                        |                |
     | 3. Request resource with Service Ticket|                |
     |-------------------------------------------------------->|
     |                                        |                |
     |                                        |                |
     | 3. Revieve access to resouces          |                |
     |<--------------------------------------------------------|
     |                                        |                |

```