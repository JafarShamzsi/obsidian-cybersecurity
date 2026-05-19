#### Overview

Open Authorization (OAuth) is an open standard protocol that provides secure delegated access to protected resources via token-based authentication. OAuth enables clients (applications or services) to access server resources on behalf of a resource owner without directly handling or storing user credentials. It is the de facto standard for securing RESTful APIs and is commonly implemented in modern web, cloud, and mobile applications.

---

#### Architectural Roles

- **Resource Owner**: The entity (typically a user) who owns the protected resources.
    
- **Client**: The application requesting access to protected resources on behalf of the resource owner.
    
- **Authorization Server**: Authenticates the resource owner and issues access tokens to the client.
    
- **Resource Server (API Server)**: Hosts the protected resources and accepts access tokens from clients to grant access.
    

---

#### OAuth Authorization Flow

1. **Client Registration**
    
    - The client registers with the authorization server.
        
    - Receives a `client_id`, `client_secret`, and a pre-defined `redirect_uri` endpoint.
        
2. **Authorization Request**
    
    - The client directs the resource owner to the authorization server.
        
    - The resource owner authenticates and consents to grant access.
        
3. **Authorization Grant Issuance**
    
    - Upon user consent, the authorization server issues an authorization grant (e.g., authorization code) to the client.
        
4. **Token Exchange**
    
    - The client presents the grant (along with its credentials) to the authorization server.
        
    - An access token (and optionally a refresh token) is issued.
        
5. **Accessing Resources**
    
    - The client sends the access token to the resource server.
        
    - If the token is valid and within scope, the requested resource is returned.
        

---

#### Grant Types (Authorization Flows)

|Flow Type|Use Case|
|---|---|
|**Authorization Code Grant**|Recommended for server-side web applications. Involves redirect-based flow and secure exchange of credentials.|
|**Implicit Grant**|Simplified, less secure flow designed for browser-based or mobile clients. Deprecated in OAuth 2.1.|
|**Resource Owner Password Credentials Grant**|Direct exchange of credentials. Suitable only when high trust exists between user and client. Not recommended.|
|**Client Credentials Grant**|Suitable for machine-to-machine communication (e.g., microservices). No user context required.|
|**Device Authorization Grant**|Designed for input-constrained devices (e.g., smart TVs, IoT). Requires manual user confirmation from a secondary device.|

---

#### Token Structure and Format

- **Access Token**: Short-lived bearer token used to authorize requests to protected APIs.
    
- **Refresh Token**: Optional long-lived token used to obtain new access tokens without reauthentication.
    
- **JWT Format (JSON Web Token)**:
    
    - **Header**: Specifies signing algorithm and token type.
        
    - **Payload**: Contains claims such as issuer (`iss`), subject (`sub`), expiration (`exp`), audience (`aud`), and scope.
        
    - **Signature**: Ensures integrity and authenticity, signed using HMAC or RSA.
        

Tokens are typically Base64 URL-encoded and transmitted via the HTTP `Authorization: Bearer <token>` header.

---

#### Security Considerations

- Always transmit tokens over TLS (HTTPS) to protect confidentiality.
    
- Store `client_secret` securely; never expose it in public repositories or frontend code.
    
- Implement proper **scope limitation** to enforce least-privilege access.
    
- Ensure token expiration and implement token revocation mechanisms.
    
- Monitor for token misuse and enforce rate limiting and logging.
    
- Rotate cryptographic signing keys regularly.
    
- Use **PKCE (Proof Key for Code Exchange)** for public clients to mitigate authorization code interception attacks.
    

---

#### Example Implementation

In an OAuth integration with Google APIs, a third-party application obtains authorization from the user to access Google Drive metadata. The app is registered with Google’s authorization server and exchanges an authorization code for an access token, which it then uses to query the Google Drive API. At no point does the app receive or store the user's Google credentials.

---

#### Related Protocols and Standards

- **OpenID Connect (OIDC)**: An identity layer built on top of OAuth 2.0 for authentication and user profile retrieval.
    
- **JWT (RFC 7519)**: Standard for claims-based security tokens used in OAuth.
    
- **RFC 6749**: The OAuth 2.0 Authorization Framework.
    
- **RFC 6750**: Bearer Token Usage in OAuth 2.0.
    



### extra note
Many public clouds use application programming interfaces (APIs) based on Representational State Transfer (REST) rather than SOAP. These are called RESTful APIs. Where SOAP is a tightly specified protocol, REST is a looser architectural framework. This allows the service provider more choice over implementation elements. Compared to SOAP and SAML, there is better support for mobile apps.

Authentication and authorization for a RESTful API are often implemented using the Open Authorization (OAuth) protocol. OAuth is designed to facilitate sharing of information (resources) within a user profile between sites. The user creates a password-protected account at an identity provider (IdP). The user can link that identity to an OAuth consumer site without giving the password to the consumer site. A user (resource owner) can grant an OAuth client authorization to access some part of their account. A client in this context is an app or consumer site.

The user account is hosted by one or more resource servers. A resource server is called an API server because it hosts the functions that allow OAuth clients (consumer sites and mobile apps) to access user attributes. An authorization server processes authorization requests. A single authorization server can manage multiple resource servers; equally, the resource and authorization server could be the same server instance.

The client app or service must be registered with the authorization server. As part of this process, the client registers a redirect URL, which is the endpoint that will process authorization tokens. Registration also provides the client with an ID and a secret. The ID can be publicly exposed, but the secret must be kept confidential between the client and the authorization server. When the client application requests authorization, the user approves the authorization server to grant the request using an appropriate method. OAuth supports several grant types—or flows—for use in different contexts, such as server to server or mobile app to server. Depending on the flow type, the client will end up with an access token validated by the authorization server. The client presents the access token to the resource server, which then accepts the request for the resource if the token is valid.

OAuth uses the JavaScript Object Notation (JSON) Web Token (JWT) format for claims data. JWTs can be passed as Base64-encoded strings in URLs and HTTP headers and can be digitally signed for authentication and integrity