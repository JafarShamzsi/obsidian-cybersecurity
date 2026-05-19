## Fundamental Principles

Asymmetric cryptography, also known as public-key cryptography, employs a pair of mathematically related keys (public and private) to secure communications. Unlike symmetric encryption which uses a single shared secret key, asymmetric algorithms leverage computational hardness assumptions to create a one-way function where:

- Information encrypted with the public key can only be decrypted with the corresponding private key
- The private key cannot be feasibly derived from the public key
- The security strength depends on the mathematical difficulty of specific problems (factorization, discrete logarithm, elliptic curve discrete logarithm)

![[Pasted image 20250509041401.png]]

## Core Mathematical Foundations

Asymmetric encryption security relies on mathematical problems that are:

1. **Computationally infeasible** to solve in reasonable time with current technology
2. **Asymmetric in computational complexity** - easy to compute in one direction but extremely difficult to reverse

### Primary Hard Problems Used:

|Problem|Description|Algorithms Based On It|
|---|---|---|
|Integer Factorization|Finding prime factors of large composite numbers|RSA|
|Discrete Logarithm|Finding exponents in modular arithmetic|Diffie-Hellman, DSA, ElGamal|
|Elliptic Curve Discrete Logarithm|Finding the scalar multiplier on an elliptic curve|ECDSA, ECDH, EdDSA|

## Key Operational Flow

The standard operational flow of asymmetric encryption:

1. **Key Generation**:
    
    - Generate mathematically linked key pair (public/private)
    - Private key uses strong entropy sources
    - Key pair generation parameters determine security strength
2. **Encryption Process**:
    
    - Sender acquires recipient's authentic public key
    - Message encrypted using recipient's public key
    - Ciphertext transmitted over potentially insecure channel
3. **Decryption Process**:
    
    - Recipient uses private key to decrypt message
    - Private key performs the mathematical inverse operation
    - Only the holder of the private key can recover plaintext

## Major Asymmetric Algorithms Analysis

### RSA (Rivest-Shamir-Adleman)

**Core Mechanism**: Security based on the practical difficulty of factoring the product of two large prime numbers.

**Key Components**:

- **Key Generation**:
    
    1. Select two large prime numbers (p, q)
    2. Compute n = p × q
    3. Calculate φ(n) = (p-1)(q-1)
    4. Select integer e where 1 < e < φ(n) and gcd(e, φ(n)) = 1
    5. Determine d such that (d × e) mod φ(n) = 1
- **Public Key**: (n, e)
    
- **Private Key**: (n, d)
    

**Encryption**: C = M^e mod n (where M is the message) **Decryption**: M = C^d mod n

**Security Considerations**:

- Recommended minimum key length: 2048 bits (3072+ bits for high security)
- Security scales with computational difficulty of factoring n
- Susceptible to quantum computing attacks via Shor's algorithm
- Implementation vulnerabilities: timing attacks, padding oracle attacks

### Elliptic Curve Cryptography (ECC)

**Core Mechanism**: Security based on the difficulty of solving the discrete logarithm problem over elliptic curves.

**Key Components**:

- **Domain Parameters**: (p, a, b, G, n, h)
    
    - p: prime that specifies the finite field
    - a, b: coefficients defining the curve equation y² = x³ + ax + b (mod p)
    - G: base point/generator point on the curve
    - n: order of G (number of points in the subgroup)
    - h: cofactor (total number of points divided by n)
- **Key Generation**:
    
    1. Select random integer d in range [1, n-1]
    2. Compute Q = d × G (point multiplication)
- **Public Key**: Q (point on the curve)
    
- **Private Key**: d (scalar value)
    

**Security Considerations**:

- 256-bit ECC roughly equivalent to 3072-bit RSA
- Significant efficiency advantages in computation, key size, and bandwidth
- Various standard curves (P-256, Curve25519, etc.) with different security properties
- Susceptible to invalid curve attacks if implementations don't validate points

### Diffie-Hellman Key Exchange (DH)

**Core Mechanism**: Allows two parties to securely establish a shared secret over an insecure channel.

**Process**:

1. Alice and Bob agree on public parameters (prime p and generator g)
2. Alice generates private key a, computes A = g^a mod p
3. Bob generates private key b, computes B = g^b mod p
4. Alice and Bob exchange A and B
5. Alice computes shared secret K = B^a mod p
6. Bob computes shared secret K = A^b mod p
7. K is mathematically equivalent for both parties: K = g^(ab) mod p

**Variants**:

- **ECDH**: Elliptic Curve Diffie-Hellman - uses ECC operations instead of modular exponentiation
- **ECDHE**: Ephemeral ECDH - generates new key pairs for each exchange (forward secrecy)

## Performance Characteristics

|Algorithm|Key Size|Encryption Speed|Decryption Speed|Signature Creation|Signature Verification|
|---|---|---|---|---|---|
|RSA-2048|2048 bits|Moderate|Slow|Slow|Fast|
|RSA-4096|4096 bits|Slow|Very Slow|Very Slow|Fast|
|ECDSA P-256|256 bits|Fast|Fast|Fast|Moderate|
|Ed25519|256 bits|Very Fast|Very Fast|Very Fast|Very Fast|

## Practical Security Considerations

### Key Length Recommendations (2025)

|Security Level|RSA Key Size|ECC Key Size|Symmetric Equivalent|
|---|---|---|---|
|Medium-term|2048 bits|224-255 bits|112 bits|
|Long-term|3072 bits|256-383 bits|128 bits|
|Foreseeable future|7680 bits|384-511 bits|192 bits|
|Post-quantum concerns|15360+ bits|512+ bits|256 bits|

### Implementation Vulnerabilities

1. **Side-Channel Attacks**:
    
    - **Timing Attacks**: Measure time variations in cryptographic operations
    - **Power Analysis**: Monitor power consumption during operations
    - **Acoustic Analysis**: Analyze sound emissions during key operations
    - **Cache Attacks**: Exploit CPU cache behavior to extract key information
2. **Implementation Flaws**:
    
    - Poor randomness in key generation
    - Insufficient protection of private keys
    - Missing validation of public keys/parameters
    - Padding oracle vulnerabilities
3. **Mitigation Techniques**:
    
    - Constant-time implementations
    - Blinding techniques for RSA operations
    - Regular key rotation
    - Hardware security modules (HSMs)
    - Proper padding schemes (OAEP, PSS)

## Hybrid Encryption Systems

Due to performance limitations of asymmetric encryption, most practical systems employ hybrid approaches:

1. **Envelope Encryption**:
    
    - Generate random symmetric key (AES-256)
    - Encrypt actual data with symmetric key
    - Encrypt symmetric key with recipient's public key
    - Transmit encrypted data and encrypted symmetric key
2. **TLS Handshake Flow**:
    
    - Asymmetric cryptography authenticates parties and negotiates session keys
    - Bulk data transmission secured with symmetric encryption
    - Perfect Forward Secrecy (PFS) achieved through ephemeral key exchanges

## Post-Quantum Considerations

Quantum computers pose significant threats to current asymmetric cryptography:

- **Quantum Threat Assessment**:
    
    - Shor's algorithm can efficiently factor large integers and solve discrete logarithm problems
    - RSA, DSA, ECC, and DH would be compromised
- **Post-Quantum Algorithms**:
    
    - **Lattice-based**: NTRU, CRYSTALS-Kyber
    - **Hash-based**: SPHINCS+
    - **Code-based**: McEliece
    - **Multivariate**: Rainbow
    - **Isogeny-based**: SIKE (compromised in 2022)
- **Transition Strategy**:
    
    - Implement crypto-agility in systems
    - Prepare for algorithm replacement
    - Consider hybrid classical/post-quantum approaches

## Common Application Scenarios

### Digital Signatures

1. **Process**:
    
    - Signer hashes document to create digest
    - Signer encrypts digest with private key
    - Verifier decrypts signature with signer's public key
    - Verifier compares decrypted digest with independently calculated digest
2. **Algorithms**:
    
    - RSA-PSS (Probabilistic Signature Scheme)
    - ECDSA (Elliptic Curve Digital Signature Algorithm)
    - EdDSA (Edwards-curve Digital Signature Algorithm)
3. **Security Properties**:
    
    - Non-repudiation
    - Integrity verification
    - Authentication of source

### Public Key Infrastructure (PKI)

1. **Components**:
    
    - Certificate Authorities (CAs)
    - Registration Authorities (RAs)
    - Certificate Revocation Lists (CRLs)
    - Online Certificate Status Protocol (OCSP)
2. **X.509 Certificates**:
    
    - Bind public keys to identities
    - Include validity periods
    - Define key usage constraints
    - Establish certificate chains/hierarchy
3. **Trust Models**:
    
    - Hierarchical PKI
    - Web of Trust
    - Bridge CA
    - Cross-certification

## Real-World Deployment Considerations

1. **Key Management Lifecycle**:
    
    - Generation with sufficient entropy
    - Secure storage (HSMs, TPMs)
    - Distribution through secure channels
    - Regular rotation policies
    - Secure destruction methods
2. **Performance Optimization**:
    
    - Hardware acceleration
    - Batch processing of operations
    - Caching strategies (with security boundaries)
    - Optimize key sizes for specific threat models
3. **Regulatory Compliance**:
    
    - FIPS 140-2/3 validation
    - Common Criteria certification
    - eIDAS compliance (EU)
    - Industry-specific standards (PCI DSS, HIPAA)

## Advanced Attack Vectors

1. **Bleichenbacher's Attack**:
    
    - Exploits PKCS#1 v1.5 padding vulnerabilities
    - Uses subtle error messages to gradually reveal information
2. **ROCA Vulnerability**:
    
    - Affects specific key generation methods
    - Allows factorization of affected RSA keys
3. **Adaptive Chosen-Ciphertext Attacks**:
    
    - Manipulates ciphertexts and observes system responses
    - Can compromise improperly implemented systems
4. **Key Extraction via Hardware/VM Vulnerabilities**:
    
    - Speculative execution side channels (Spectre, Meltdown)
    - Cache timing attacks across VM boundaries
    - Cold boot attacks on memory containing keys

## Best Practices Summary

1. **Algorithm Selection**:
    
    - Use established, well-reviewed algorithms (RSA, ECDSA, EdDSA)
    - Favor ECC for constrained environments
    - Implement crypto-agility for future algorithm transitions
2. **Key Management**:
    
    - Generate keys with cryptographically secure random number generators
    - Store private keys in hardware security modules when possible
    - Implement strong access controls for key material
    - Establish key rotation schedules based on risk assessment
3. **Implementation Security**:
    
    - Use validated cryptographic libraries (OpenSSL, Libsodium, BouncyCastle)
    - Apply constant-time coding practices
    - Validate all inputs including public keys
    - Implement proper padding schemes (OAEP for encryption, PSS for signatures)
4. **Operational Security**:
    
    - Regularly audit cryptographic implementations
    - Monitor for compromise indicators
    - Maintain secure key backup procedures
    - Establish key compromise response plans

---

_This technical note represents current best practices as of May 2025. Cryptographic recommendations evolve with advances in computing power and cryptanalysis. Regular review and updates are essential._