### Overview

Perfect Forward Secrecy (PFS) is a security property of cryptographic protocols that ensures **past session keys cannot be recovered**, even if long-term private keys (e.g., a server’s RSA private key) are later compromised. This provides **retrospective confidentiality**, preventing stored encrypted communications from being decrypted if the attacker later gains access to the private key material.

PFS is achieved using **ephemeral key exchanges**, most notably:

- **DHE**: Diffie-Hellman Ephemeral
    
- **ECDHE**: Elliptic Curve Diffie-Hellman Ephemeral
    

These ephemeral methods generate unique session keys per connection that are not stored long-term.

---

### Threat Model Addressed

Without PFS:

- Sessions negotiated using non-ephemeral RSA or static DH can be decrypted if the server’s private key is compromised.
    
- Adversaries (e.g., nation-states) can **passively record encrypted traffic**, store it, and decrypt it at a later date upon key compromise.
    

With PFS:

- Ephemeral session keys are generated per session and **never stored**.
    
- Even if an attacker obtains the server’s private key or future keying material, **previous sessions remain confidential**.
    

---

### Diffie-Hellman Key Exchange (Classic DHE)

Diffie-Hellman allows two parties (Alice and Bob) to **derive a shared symmetric secret** over an insecure channel without transmitting the secret directly.

#### Public Parameters

- `p`: a large prime number
    
- `g`: a primitive root modulo `p` (generator)
    

These values are public and can be reused.

#### Key Agreement Procedure

Assume:

- `p = 23`
    
- `g = 9`
    

1. Alice generates a private key `a = 5`, computes public key `A = g^a mod p = 9^5 mod 23 = 8`, and sends `A` to Bob.
    
2. Bob generates a private key `b = 3`, computes public key `B = g^b mod p = 9^3 mod 23 = 16`, and sends `B` to Alice.
    
3. Alice computes the shared secret: `s = B^a mod p = 16^5 mod 23 = 6`
    
4. Bob computes the shared secret: `s = A^b mod p = 8^3 mod 23 = 6`
    

Thus, both parties independently derive the same symmetric key `s = 6`.

An eavesdropper (Mallory) who sees `p`, `g`, `A`, and `B` cannot compute `s` unless she solves the **discrete logarithm problem (DLP)**, which is computationally infeasible for large `p`.

![[Pasted image 20250513035438 1.png]]

---

### Ephemeral vs Static Diffie-Hellman

|Key Exchange Type|Session Key Reuse|Forward Secrecy|Performance|Use Case|
|---|---|---|---|---|
|Static DH|Reused|❌|Moderate|Deprecated|
|Ephemeral DH (DHE)|Per-session|✅|Slower|TLS 1.2 (legacy)|
|Ephemeral ECDH (ECDHE)|Per-session|✅|Efficient|TLS 1.2/1.3|

Only **ephemeral variants (DHE/ECDHE)** support Perfect Forward Secrecy.

---

### Elliptic Curve Diffie-Hellman Ephemeral (ECDHE)

ECDHE improves upon classic DHE by using **elliptic curve mathematics**. Benefits include:

- Smaller key sizes for equivalent security (e.g., 256-bit ECC ≈ 3072-bit RSA)
    
- Faster computations (fewer CPU cycles)
    
- Lower bandwidth usage
    

Example:

- Curve: `secp256r1`
    
- Each party selects a private scalar `k` and computes a public point `K = kG`
    
- The shared secret is derived via scalar multiplication using the peer’s public key
    

TLS cipher suite example: `TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256`

---

### PFS in TLS

- **TLS 1.2**: PFS is optional, depending on the cipher suite. Must use `(EC)DHE` to get PFS.
    
- **TLS 1.3**: PFS is **mandatory**. All key exchanges are ephemeral.
    

Server-side requirements:

- Use a secure, modern TLS stack (e.g., OpenSSL ≥ 1.1.1)
    
- Disable static RSA key exchange
    
- Prefer ECDHE suites with strong AEAD ciphers (AES-GCM, ChaCha20-Poly1305)
    
- Rotate Diffie-Hellman parameters regularly (when not using named curves)
    

---

### Attack Surface and Implementation Considerations

- **Weak DH Groups**: Ensure 2048-bit or stronger primes. Avoid export-grade 512-bit groups.
    
    - Use RFC 7919 predefined DH groups.
        
- **Logjam Attack**: Exploits common prime reuse and weak DH groups. Mitigated by enforcing strong groups and disabling export ciphers.
    
- **Parameter Validation**: Implementers must validate received DH/ECDH parameters to prevent small subgroup attacks.
    
- **Side-Channel Attacks**: Implementations must use constant-time arithmetic for scalar operations in ECDH.
    

---

### PFS and Digital Envelopes

In traditional "digital envelope" systems:

- A symmetric session key is encrypted with the recipient's public RSA key.
    
- If the RSA private key is later compromised, the envelope can be decrypted retroactively.
    

With PFS:

- The session key is **not sent or encrypted directly**.
    
- Instead, it is **ephemerally derived** using (EC)DHE.
    
- Even if the server’s private signing key is compromised, prior session keys cannot be computed.