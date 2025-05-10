## Concepts

Public Key Infrastructure (PKI) serves as the foundational trust framework enabling secure digital communications across untrusted networks. At its core, PKI addresses the fundamental challenge in asymmetric cryptography: **proving cryptographic identity corresponds to real-world identity**.

### Asymmetric Cryptography Review

- **Key Pair Structure**: Based on mathematically-linked key pairs with computationally infeasible reverse derivation
    - Private Key: Must remain secret, compromise undermines entire security model
    - Public Key: Distributed freely, derived from private key via one-way function
- **Security Operations**:
    - Confidentiality: Public key encrypts → Private key decrypts
    - Authentication & Integrity: Private key signs → Public key verifies
    - Non-repudiation: Signatures mathematically tied to signer's private key

### The Key Distribution Problem

While asymmetric cryptography solves the initial key exchange problem of symmetric systems, it introduces a critical vulnerability: **the public key authentication gap**. Without verification mechanisms, threat actors can execute Man-in-the-Middle (MITM) attacks by:

1. Intercepting legitimate public key distribution
2. Substituting malicious public keys
3. Establishing separate encrypted channels with each party
4. Decrypting, inspecting/modifying, then re-encrypting communications

## Certificate Authorities: Technical Implementation

Certificate Authorities (CAs) exist to bridge the authentication gap through cryptographic attestation using hierarchical trust chains.

### X.509 Certificate Structure

Certificates follow the X.509 standard (RFC 5280) containing:

```
Certificate
├── Version
├── Serial Number (unique per CA)
├── Signature Algorithm (typically RSA-SHA256 or ECDSA)
├── Issuer DN (Distinguished Name of issuing CA)
├── Validity
│   ├── Not Before
│   └── Not After
├── Subject DN (Entity being certified)
├── Subject Public Key Info
│   ├── Algorithm
│   └── Public Key
├── X.509v3 Extensions
│   ├── Key Usage
│   ├── Extended Key Usage
│   ├── Basic Constraints
│   ├── Subject Alternative Name (SAN)
│   └── Certificate Policies
└── Certificate Signature
```

### CA Hierarchy & Trust Models

#### Root CAs

- Self-signed certificates (issuer = subject)
- Offline storage in air-gapped HSMs (Hardware Security Modules)
- 4096-bit RSA keys or ECC P-384/P-521 curves
- 20+ year validity periods
- Protected by strict physical and procedural controls
- Distributed in OS/browser trusted certificate stores

#### Intermediate CAs

- Signed by Root CA or higher-level Intermediate
- Online but highly secured infrastructure
- 4096-bit RSA keys or ECC P-256/P-384 curves
- 5-10 year validity periods
- Used for operational certificate issuance
- Creates defense-in-depth via certificate path validation

#### Cross-Certification

- Enables trust between separate PKI domains
- Implemented through bi-directional or uni-directional cross-certificates
- Critical for interoperability between organizational PKIs

## Certificate Lifecycle Management

### 1. Certificate Request & Validation

**Certificate Signing Request (CSR) Structure:**

```
CertificationRequest ::= SEQUENCE {
    certificationRequestInfo CertificationRequestInfo,
    signatureAlgorithm AlgorithmIdentifier,
    signature BIT STRING }
```

**Domain Validation (DV) Methods:**

- HTTP-01: Specific content at `/.well-known/acme-challenge/`
- DNS-01: Specific TXT record
- TLS-ALPN-01: Special TLS handshake

**Extended Validation (EV) Requirements:**

- Business registration verification
- Physical address verification
- Telephone verification
- Domain ownership verification
- Legal authorization verification

### 2. Certificate Issuance

1. CA validates the identity according to Certificate Policy
2. CA generates certificate with unique serial number
3. Certificate signed using CA's private key
4. Certificate delivered via secure channel
5. Certificate published to certificate transparency logs

### 3. Certificate Revocation

Methods:

- **Certificate Revocation Lists (CRLs)**
    
    - Periodic batch publication
    - RFC 5280 compliant
    - Distribution points specified in certificates
    - Susceptible to lag time
- **Online Certificate Status Protocol (OCSP)**
    
    - Real-time status checking
    - RFC 6960 compliant
    - Signed responses from OCSP responders
    - Privacy concerns with "OCSP stapling" as mitigation
- **OCSP Must-Staple**
    
    - X.509 extension requiring stapled OCSP response
    - Forces revocation checking
    - Mitigates soft-fail behavior

Common revocation reasons:

- Key compromise
- CA compromise
- Affiliation changed
- Superseded
- Cessation of operation

## Certificate Transparency

Certificate Transparency (CT) provides public auditability of issued certificates, implemented as:

- **Append-only Merkle Hash Trees**
- **Multiple independent, publicly-verifiable logs**
- **SCTs (Signed Certificate Timestamps)** embedded in certificates
- **Monitors** watching for suspicious certificates
- **Auditors** verifying log consistency

CT effectively prevents:

- Rogue certificate issuance
- CA compromise going undetected
- Targeted MITM attacks with fraudulent certificates

## Cryptographic Agility & Security Considerations

### Algorithm Selection

- **Signing Algorithms**:
    
    - RSA (2048+ bits)
    - ECDSA (P-256, P-384)
    - EdDSA (Ed25519, Ed448)
- **Hash Functions**:
    
    - SHA-256 (minimum)
    - SHA-384 (recommended for high-security)

### Common Attacks & Mitigations

1. **Certificate Spoofing**
    
    - Prevention: Certificate pinning, DANE, CT verification
2. **CA Compromise**
    
    - Prevention: Multi-vetting, HSMs, network segmentation
3. **Weak Key Generation**
    
    - Prevention: Proper entropy sources, strong RNG
4. **Implementation Vulnerabilities**
    
    - Prevention: Code audits, fuzzing, formal verification
5. **Name Constraints Bypass**
    
    - Prevention: Proper name constraint validation

## Automated Certificate Management

Modern certificate management leverages automation via protocols like ACME (RFC 8555):

1. Client proves domain control
2. Server issues certificate automatically
3. Certificates can be auto-renewed
4. Minimal human intervention needed

Implementations include Let's Encrypt, ZeroSSL, and enterprise CA automation systems.

## Enterprise PKI Considerations

### Internal CA Deployment

- Root CA in offline, air-gapped hardware
- Intermediate CAs for different purposes:
    - TLS Web Server Authentication
    - Code Signing
    - Document Signing
    - Email Security (S/MIME)

### Certificate Policy (CP) & Certification Practice Statement (CPS)

- **CP**: High-level organizational requirements
- **CPS**: Detailed implementation practices
- Must comply with CA/Browser Forum Baseline Requirements for public trust

## Advanced PKI Applications

### mTLS (Mutual TLS)

- Both server and client authenticated via certificates
- Commonly used in microservices, API security
- Provides stronger security than password-based authentication

### Code Signing

- Executable code signed with developer certificates
- Chain of trust verified during execution
- Prevents malware distribution

### Document Signing

- Non-repudiation for contracts, agreements
- Long-term validation with timestamp services
- Often requires qualified certificates (eIDAS in EU)

## Forensic Analysis of Certificate-Based Incidents

1. Certificate chain collection and validation
2. Certificate transparency log analysis
3. HSM audit log examination
4. Network traffic analysis for certificate exchanges
5. Timeline reconstruction of certificate operations

---

## References & Further Reading

1. RFC 5280: X.509 PKI Certificate and CRL Profile
2. RFC 6960: Online Certificate Status Protocol
3. RFC 8555: Automatic Certificate Management Environment (ACME)
4. CA/Browser Forum Baseline Requirements
5. NIST SP 800-57: Recommendation for Key Management
6. [Certificate Transparency](https://certificate.transparency.dev/)
7. [Let's Encrypt](https://letsencrypt.org/how-it-works/)