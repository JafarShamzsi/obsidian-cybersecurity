### Overview

**Blockchain** is a distributed, append-only ledger technology that ensures the **integrity, transparency, and immutability** of data records—typically transactions—through cryptographic linkage of blocks. This system is **decentralized** and **trustless**, eliminating the need for centralized authorities or intermediaries in data validation.

---

### 1. Structure of a Blockchain

A blockchain consists of a **chronological chain of blocks**, each of which contains:

- **Transaction Data**: Payload such as financial transfers, contracts, or any arbitrary record.
    
- **Timestamp**: Time the block was mined or validated.
    
- **Previous Block Hash**: Cryptographic hash of the preceding block in the chain.
    
- **Nonce** (in proof-of-work systems): A number used once that satisfies the system’s difficulty requirement.
    
- **Current Block Hash**: The resulting hash of the block's content, used as a reference by the next block.
    

Each block's hash is a **digest of its entire content** including the hash of the previous block, creating a **cryptographic linkage**. 
Formally:
```
Block_N = {
    data,
    timestamp,
    previous_hash,
    nonce
}
hash_N = SHA-256(Block_N)

```

This chaining of hashes ensures that **any change in a past block** alters its hash, thereby **breaking the chain** from that point forward—making tampering evident and computationally expensive to conceal.

---

### 2. Cryptographic Integrity

Blockchain security hinges on **cryptographic hash functions** such as SHA-256:

- **Deterministic**: Same input → same output
    
- **Pre-image resistant**: Infeasible to derive input from output
    
- **Collision resistant**: Unlikely two different inputs produce same hash
    
- **Avalanche effect**: Small changes in input produce drastically different output
    

Tampering with a block changes its hash → subsequent block becomes invalid → full chain requires recomputation.

---

### 3. Decentralization and Distributed Ledger

#### 3.1 Peer-to-Peer (P2P) Network

Blockchain nodes form a **distributed peer-to-peer network**. Each node:

- Holds a **full or partial copy** of the blockchain
    
- Participates in block validation and consensus
    
- Propagates new transactions and blocks
    

Benefits of decentralization:

- **No single point of failure**
    
- **Resilience against tampering or corruption**
    
- **Redundancy of data storage**
    
- **Trustless interaction** (participants don't need to know or trust each other)
    

#### 3.2 Public vs. Private Blockchains

|Type|Access Control|Use Case Examples|
|---|---|---|
|**Public**|Open to all|Bitcoin, Ethereum|
|**Private**|Restricted|Enterprise supply chains, banking|
|**Consortium**|Shared control|Industry-specific platforms (e.g., Hyperledger)|

---

### 4. Consensus Mechanisms

Blockchain relies on **consensus algorithms** to agree on the valid state of the ledger across all nodes.

#### Common Consensus Mechanisms:

|Mechanism|Description|
|---|---|
|**Proof of Work (PoW)**|Nodes solve computational puzzles (mining) to validate blocks. Energy-intensive but secure. Used in Bitcoin.|
|**Proof of Stake (PoS)**|Validators are chosen based on the amount of cryptocurrency they "stake". Energy-efficient. Used in Ethereum 2.0.|
|**Delegated PoS / BFT**|Voting-based consensus, used in permissioned blockchains. Faster but centralized risk.|

---

### 5. Security Properties

|Property|Achieved Through|Notes|
|---|---|---|
|**Immutability**|Hash chaining, consensus rules|Altering a block breaks chain integrity|
|**Integrity**|Digital signatures, hashes|Ensures data has not been tampered with|
|**Availability**|Decentralization, P2P replication|Resistant to DoS and data loss|
|**Non-repudiation**|Digital signatures of transaction originators|Users cannot deny submitted transactions|
|**Transparency**|Public ledgers|All participants can verify historical data|

---

### 6. Attack Vectors and Mitigation

|Attack Type|Description|Mitigation|
|---|---|---|
|**51% Attack**|If a single entity controls >50% of the network’s hashing/staking power, they can double-spend or censor transactions|Requires immense resources in large networks|
|**Sybil Attack**|Malicious actor spawns many fake nodes to influence consensus|Identity verification, stake requirements|
|**Replay Attack**|Re-sending a previously valid transaction in another context|Use of unique identifiers or nonces|
|**Smart Contract Vulnerabilities**|Logic flaws in smart contracts|Formal verification, security audits|

---

### 7. Applications of Blockchain

- **Cryptocurrency**: Bitcoin, Ethereum, Monero
    
- **Smart Contracts**: Self-executing code embedded in the chain (Ethereum)
    
- **Supply Chain Tracking**: Provenance and tamper-proof audit trails
    
- **Identity Management**: Decentralized identifiers (DIDs), self-sovereign identity
    
- **Digital Voting Systems**: Transparent and tamper-resistant electoral processes
    
- **Digital Rights Management (DRM)**: Copyright tracking, IP verification
    
- **Secure Medical Records**: Auditability and access control over health data
    

---

### 8. Key Limitations

- **Scalability**: Limited throughput (transactions per second) compared to centralized systems
    
- **Latency**: Consensus delays introduce confirmation time
    
- **Storage Bloat**: Blockchain size grows continuously
    
- **Regulatory Uncertainty**: Especially in finance and identity use cases
    
- **Energy Consumption**: Significant in PoW systems (e.g., Bitcoin)
    

---

### 9. Code Example (Simplified Python Blockchain Prototype)

```
import hashlib
import time

class Block:
    def __init__(self, index, previous_hash, data, timestamp=time.time()):
        self.index = index
        self.timestamp = timestamp
        self.data = data
        self.previous_hash = previous_hash
        self.hash = self.compute_hash()

    def compute_hash(self):
        block_string = f"{self.index}{self.timestamp}{self.data}{self.previous_hash}"
        return hashlib.sha256(block_string.encode()).hexdigest()

# Genesis block
blockchain = [Block(0, "0", "Genesis Block")]

# Adding a new block
def add_block(data):
    previous_block = blockchain[-1]
    new_block = Block(len(blockchain), previous_block.hash, data)
    blockchain.append(new_block)

add_block("Alice pays Bob 5 BTC")
add_block("Bob pays Charlie 2 BTC")>)
```

---

### 10. References

- Nakamoto, S. (2008). _Bitcoin: A Peer-to-Peer Electronic Cash System_
    
- Ethereum Whitepaper: https://ethereum.org/en/whitepaper/
    
- NIST IR 8202: _Blockchain Technology Overview_
    
- OWASP Blockchain Security Guide
    
- Hyperledger Architecture: [https://www.hyperledger.org/](https://www.hyperledger.org/)