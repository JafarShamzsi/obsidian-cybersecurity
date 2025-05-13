### Overview

In cryptographic systems, particularly those involving **password-based authentication or encryption**, the use of **salting** and **key stretching** is critical to mitigate attacks arising from low-entropy secrets. These techniques are designed to **enhance the security of password-derived secrets**, which are inherently weak due to human-generated passwords typically being short, predictable, and reused.

---

### 1. Entropy and the Problem of Human Passwords

**Entropy** refers to the level of unpredictability or randomness in a system. High-entropy keys (e.g., 256-bit cryptographically random strings) are computationally infeasible to guess via brute force. In contrast, human-generated passwords have **low entropy**:

- Limited character space (e.g., lowercase only)
    
- Short length (often <12 characters)
    
- Predictable patterns (dictionary words, common substitutions)
    

This makes **offline attacks** such as brute-force and dictionary-based cracking viable, especially when combined with **precomputed hash tables** (rainbow tables).

---

### 2. Hashing for Password Storage

Hashing is a one-way cryptographic function:

- Input: `password`
    
- Output: fixed-length hash digest `H(password)`
    

Characteristics:

- Deterministic: same input → same output
    
- One-way: infeasible to reverse
    
- Collision-resistant (ideal): two different inputs should not produce the same hash
    

**Issue**: A hash alone does **not hide** the fact that users may use common or identical passwords. Without further protection, the hash is vulnerable to:

- **Brute-force attacks**: Try all combinations
    
- **Dictionary attacks**: Use common wordlists
    
- **Rainbow table attacks**: Use precomputed tables of hashes for common passwords
    

---

### 3. Salting

#### 3.1 Definition

A **salt** is a unique, cryptographically secure random string that is concatenated to the password **before hashing**.

Formally:

`salt = Random(128 bits or more) hash = H(salt || password)`

The salt must be:

- **Unique per user** (per credential record)
    
- **Random** and **long enough** (≥128 bits)
    
- **Stored in plaintext** alongside the hash (it is not secret)
    

#### 3.2 Purpose and Benefits

- **Uniqueness of hashes**: Prevents identical passwords from having the same hash.
    
- **Rainbow table mitigation**: Precomputed tables become useless; attacker would need a unique table for each salt value.
    
- **Personalized attacks become expensive**: Attackers must re-hash every guess per unique salt, slowing down mass attacks.
    

#### 3.3 Storage Format (Example)

```
user: alice
salt: 3f5a23c9e7b45abce3921f0e
hash: a48e7340cd567d3f9b0f3d4bb7495d1a

```

Salt can be stored as a prefix in the final hash string (e.g., in Base64 or hex), such as:


```
$salt$hash
```

---

### 4. Key Stretching

#### 4.1 Definition

**Key stretching** is a method to transform a weak input (like a password) into a stronger cryptographic key by **repeated processing** (e.g., thousands of hashing rounds). The intent is to make brute-force and dictionary attacks **computationally expensive**.

#### 4.2 Why Key Stretch?

- Brute-force attacks on low-entropy inputs (e.g., passwords) are fast with modern hardware.
    
- Key stretching **increases computation time per guess**, reducing the feasibility of mass guessing attacks.
    

Key stretching does **not** increase entropy, but it:

- **Raises the cost** of each trial for the attacker
    
- **Creates a time-complexity bottleneck** per password attempt
    

#### 4.3 Common Key Stretching Algorithms

| Algorithm  | Description                                                                                                                                                |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **PBKDF2** | Password-Based Key Derivation Function 2. Applies a hash function (e.g., HMAC-SHA256) repeatedly (`n` iterations). Widely supported (e.g., WPA2, OpenSSL). |
| **bcrypt** | Based on Blowfish cipher. Includes salting and cost factor. Resistant to GPU/ASIC acceleration due to memory-intensive operations.                         |
| **scrypt** | Memory-hard function designed to resist FPGA/GPU attacks. Good for environments with sensitive password use (e.g., cryptocurrency wallets).                |
| **Argon2** | Winner of the Password Hashing Competition (PHC). Default choice for modern systems. Supports configurable time, memory, and parallelism costs.            |

---

### 5. PBKDF2 Example

**Parameters:**

- `password`: User-provided secret
    
- `salt`: Cryptographically random value (≥128 bits)
    
- `iterations`: Typically ≥100,000 (depends on system policy)
    
- `H`: Underlying hash (e.g., SHA-256)
    
- `dkLen`: Desired key length in bits
    

**Function:**

`DK = PBKDF2(H, password, salt, iterations, dkLen)`

**Output**: A derived key (e.g., 256-bit key) usable for symmetric encryption or secure storage.

**Security Note**: The number of iterations must scale with Moore’s Law to retain resistance against increasing hardware speed.

---

### 6. Threat Mitigation Summary

|Threat|Mitigated By|Notes|
|---|---|---|
|Precomputed hash attacks (rainbow tables)|Salting|Salt must be unique and long enough|
|Brute-force attacks|Key stretching|Raises compute time per guess|
|Credential stuffing (reusing passwords across accounts)|Salting|Same password → different hash values|
|Hash collision exploitation|Strong hash function|Use SHA-256 or stronger|

---

### 7. Security Best Practices

- Use **strong cryptographic hash functions** (avoid MD5, SHA-1)
    
- Always **generate salts with CSPRNGs** (Cryptographically Secure Pseudo-Random Number Generators)
    
- Store salt and hash **together** (salt is not a secret)
    
- Choose key stretching algorithms based on the threat model:
    
    - PBKDF2 for compatibility
        
    - bcrypt/scrypt/Argon2 for stronger resistance
        
- Adjust iteration count periodically to match increasing hardware speeds
    

---

### 8. Implementation Considerations

- Never roll your own crypto: Use vetted libraries (e.g., OpenSSL, libsodium, BouncyCastle)
    
- Salt must be generated per password, not globally reused
    
- Don’t truncate hash outputs unnecessarily
    
- In high-security systems (e.g., password vaults, password-based key encryption), prefer **Argon2id** with high memory/time costs
    

---

### 9. Example Code (Python + hashlib + pbkdf2_hmac)

``` python
import hashlib, os

# Parameters
password = b"correcthorsebatterystaple"
salt = os.urandom(16)
iterations = 200000
key_length = 32

# Key Derivation
dk = hashlib.pbkdf2_hmac('sha256', password, salt, iterations, dklen=key_length)
print(dk.hex())

```

---

### References

- RFC 8018: PKCS #5: Password-Based Cryptography Specification v2.1
    
- OWASP Password Storage Cheat Sheet (search with omnisearch tool.)
    
- NIST SP 800-132: Recommendation for Password-Based Key Derivation
    
- Password Hashing Competition (PHC): [https://password-hashing.net/](https://password-hashing.net/)
    
- Argon2 specification: https://datatracker.ietf.org/doc/html/draft-irtf-cfrg-argon2