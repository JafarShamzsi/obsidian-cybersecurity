### Definition

**Key Length**: The number of bits in a cryptographic key, determining the size of the keyspace and thus the computational complexity required for brute force attacks.

### Mathematical Representation

- Keyspace size = 2^(key length)
- Example: 128-bit key → 2^128 possible keys ≈ 3.4 × 10^38

## Symmetric Ciphers

### Simple Example: Substitution Ciphers

- **ROT13**: Fixed key (K=13), keyspace = 25
- Key range: ROT1 to ROT25
- ROT0 and ROT26+ are considered weak keys (ROT26 = ROT0 = plaintext)
- Mathematical properties: ROT(n mod 26) where n > 0

### Advanced Encryption Standard (AES)

- **AES-128**: 128-bit key length
    - Keyspace: 2^128 ≈ 3.4 × 10^38
    - Memory requirement: 16 bytes per key
- **AES-256**: 256-bit key length
    - Keyspace: 2^256 ≈ 1.1 × 10^77
    - Memory requirement: 32 bytes per key
    - _Not_ twice as secure as AES-128, but 2^128 times more secure

## Security Implications

### Brute Force Resistance

- Computational complexity scales exponentially with key length
- Doubling key length squares the number of possible keys
- Each additional bit doubles the keyspace

### Time Complexity Analysis

Given current computational capabilities:

- 64-bit keys: Breakable with specialized hardware
- 128-bit keys: Computationally infeasible with classical computers
- 256-bit keys: Secure against quantum computing threats (Grover's algorithm reduces effective security to 2^128)

### Performance Trade-offs

- Larger keys require:
    - More memory allocation
    - Additional processor cycles
    - Increased power consumption
    - Longer encryption/decryption times

## Key Generation Requirements

### Entropy Sources

- True random number generators (TRNG)
- Cryptographically secure pseudorandom number generators (CSPRNG)
- Minimum entropy requirements proportional to key length

### Key Derivation

- Key derivation functions (KDFs) transform passwords into fixed-length keys
- Salt and iteration count parameters increase resistance to precomputation attacks

## Standard Key Lengths (2025)

|Algorithm Type|Minimum Secure Length|Recommended Length|Future-Proof Length|
|---|---|---|---|
|Symmetric|128 bits|256 bits|256 bits|
|RSA|2048 bits|3072 bits|4096 bits|
|ECC|256 bits|384 bits|521 bits|

## Related Concepts

- Key stretching
- Key rotation policies
- Forward secrecy
- Key management systems

## References

- NIST Special Publication 800-57: Recommendation for Key Management
- RFC 8446: The Transport Layer Security (TLS) Protocol Version 1.3