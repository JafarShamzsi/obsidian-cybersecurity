
#### Definition

**Security Assertion Markup Language (SAML)** is an XML-based open standard used for exchanging authentication and authorization data between security domains—specifically, between an **Identity Provider (IdP)** and a **Service Provider (SP)**. It is a foundational protocol in federated identity systems, enabling **Single Sign-On (SSO)** across disparate web applications and organizational boundaries.

SAML is maintained by **OASIS (Organization for the Advancement of Structured Information Standards)** and is currently at **version 2.0**, which introduced significant improvements over SAML 1.1, including support for multiple protocols and bindings, richer assertion contexts, and enhanced interoperability.

---

#### Architecture Components

|Component|Description|
|---|---|
|**Principal**|The user attempting to access a resource.|
|**Identity Provider (IdP)**|Authenticates the principal and issues SAML assertions.|
|**Service Provider (SP)**|Relies on assertions from the IdP to grant access.|
|**Assertion**|The XML document containing claims about the principal's identity, authentication context, and attributes.|
|**Binding**|The transport mechanism (HTTP-POST, HTTP-Redirect, HTTP-Artifact, SOAP) used to communicate SAML messages.|
|**Protocol**|The sequence of operations (e.g., SSO, Single Logout) defined by SAML.|

---

#### SAML Workflow (Web Browser SSO Profile)

1. **User Initiates Access**: The user attempts to access a resource on the SP.
    
2. **SP Issues AuthnRequest**: The SP generates a SAML Authentication Request and redirects the user to the IdP.
    
3. **IdP Authenticates User**: The user provides credentials to the IdP.
    
4. **IdP Issues SAML Response**: The IdP creates a digitally signed `<samlp:Response>` containing one or more `<saml:Assertion>` elements and redirects the user back to the SP via their browser.
    
5. **SP Validates Assertion**: The SP verifies the XML signature, checks conditions (e.g., timestamps, audience), and extracts identity/authorization information.
    
6. **Access Granted**: The SP creates a local session and grants the user access based on the received attributes.
    

---

#### Example: SAML 2.0 Assertion Snippet

```xml
<samlp:Response xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"
                xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"
                ID="200" Version="2.0"
                IssueInstant="2020-01-01T20:00:10Z"
                Destination="https://sp.foo/saml/acs"
                InResponseTo="100">

  <saml:Issuer>https://idp.foo/sso</saml:Issuer>
  <ds:Signature>...</ds:Signature>
  <samlp:Status>...</samlp:Status>

  <saml:Assertion ID="2000" Version="2.0" IssueInstant="2020-01-01T20:00:09Z">
    <saml:Issuer>https://idp.foo/sso</saml:Issuer>
    <ds:Signature>...</ds:Signature>

    <saml:Subject>...</saml:Subject>
    <saml:Conditions>
      <saml:AudienceRestriction>
        <saml:Audience>https://sp.foo</saml:Audience>
      </saml:AudienceRestriction>
    </saml:Conditions>

    <saml:AuthnStatement AuthnInstant="2020-01-01T19:59:55Z">
      ...
    </saml:AuthnStatement>

    <saml:AttributeStatement>
      <saml:Attribute Name="email">
        <saml:AttributeValue>user@example.com</saml:AttributeValue>
      </saml:Attribute>
      <saml:Attribute Name="role">
        <saml:AttributeValue>admin</saml:AttributeValue>
      </saml:Attribute>
    </saml:AttributeStatement>
  </saml:Assertion>
</samlp:Response>
```

---

#### Security Properties

|Property|Description|
|---|---|
|**Integrity**|Ensured using XML digital signatures (`<ds:Signature>`) signed with the IdP’s private key.|
|**Confidentiality**|Optional encryption of assertions using XML Encryption, often with the SP's public key.|
|**Authentication Context**|Describes how the user was authenticated (e.g., password, MFA) in the `<AuthnContext>` element.|
|**Replay Prevention**|Controlled via `IssueInstant`, `NotBefore`, and `NotOnOrAfter` conditions.|
|**Audience Restriction**|Specifies that the assertion is valid only for a particular SP (`<AudienceRestriction>`).|

---

#### Advantages

- **Cross-Domain SSO**: Enables seamless authentication across multiple service providers.
    
- **No Credential Propagation**: Credentials are never shared with the SP.
    
- **Standards-Based**: Interoperable across many platforms and vendors.
    
- **Extensible**: Supports custom attributes and flexible authentication contexts.
    

---

#### Real-World Example

**Amazon Web Services (AWS)** operates as a **SAML 2.0 Service Provider**, allowing enterprises to federate user authentication via internal IdPs (e.g., Microsoft ADFS, Okta). AWS Identity and Access Management (IAM) roles can be assumed based on SAML attributes, without the need to create IAM users per individual.

---

#### Security Risks and Exploits

|Threat|Description|
|---|---|
|**Signature Wrapping**|XML-based attack where attacker wraps valid signatures around malicious assertions.|
|**Replay Attacks**|Exploiting weak or missing time-based validation on assertions.|
|**Misconfigured Audience**|SP fails to validate the audience in the assertion.|
|**Trust Mismanagement**|SP incorrectly trusts an unverified or compromised IdP.|
|**Man-in-the-Middle (MitM)**|If SAML assertions are not transmitted over HTTPS, they can be intercepted and reused.|

---

#### Mitigations

- Always use **HTTPS/TLS** for all SP and IdP endpoints.
    
- Validate **digital signatures** using trusted certificates.
    
- Enforce **strict timestamp and audience checks**.
    
- Use **short-lived assertions** and avoid persistent tokens unless necessary.
    
- Enable **logging and alerting** on all federation events.
    
- Regularly rotate and manage signing/encryption certificates securely.
    

---

#### Summary

SAML 2.0 is a mature, robust protocol for implementing federated authentication and SSO in enterprise and cloud environments. However, its complexity and reliance on XML introduce unique security challenges that require precise configuration and rigorous validation. Properly implemented, SAML can significantly reduce identity sprawl and improve both security and user experience.
