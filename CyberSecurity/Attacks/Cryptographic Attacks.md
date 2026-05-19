Attacks that target authentication systems often depend on the system using weak cryptography.

### Downgrade Attacks

A downgrade attack makes a server or client use a lower specification protocol with weaker ciphers and key lengths. For example, a combination of an on-path and downgrade attack on HTTPS might try to force the client to use a weak version of transport layer security (TLS) or even downgrade to the legacy secure sockets layer (SSL) protocol. This makes it easier for a threat actor to force the use of weak cipher suites and forge the signature of a certificate authority that the client trusts.

A type of downgrade attack is used to attack Active Directory. A Kerberoasting attack attempts to discover the passwords that protect service accounts by obtaining service tickets and subjecting them to brute force password cracking attacks. If the credential portion of the service ticket is encrypted using AES, it is very hard to brute force. If the attack is able to cause the server to return the ticket using weak RC4 encryption, a cracker is more likely to be able to extract the service password.

Evidence of downgrade attacks is likely to be found in server logs or by intrusion detection systems.

### Collision Attacks

A collision is where a weak cryptographic hashing function or implementation allows the generation of the same digest value for two different plaintexts. A collision attack exploits this vulnerability to forge a digital signature. The attack works as follows:

1. The attacker creates a malicious document and a benign document that produce the same hash value. The attacker submits the benign document for signing by the target.
2. The attacker then removes the signature from the benign document and adds it to the malicious document, forging the target's signature.

A collision attack could be used to forge a digital certificate to spoof a trusted website or to make it appear as though Trojan malware derived from a trusted publisher.

### Birthday Attacks

A collision attack depends on being able to create a malicious document that outputs the same hash as the benign document. Some collision attacks depend on being able to manipulate the way the hash is generated. A birthday attack is a means of exploiting collisions in hash functions through brute force. Brute force means attempting every possible combination until a successful one is achieved. The attack is named after the birthday paradox. This paradox shows that the computational time required to brute force a collision might be less than expected.

The birthday paradox asks how large must a group of people be so that the chance of two of them sharing a birthday is 50%. The answer is 23, but people who are not aware of the paradox often answer around 180 (365/2). The point is that the chances of someone sharing a particular birthday are small, but the chances of any two people in a group sharing any birth date in a calendar year get better and better as you add more people: 1 – (365 * (365 _−_ 1) * (365 – 2) ... * (365 – ( _N −_ 1)/365 _N_ ) .

To exploit the paradox, the attacker creates multiple malicious and benign documents, both featuring minor changes (punctuation, extra spaces, and so on). Depending on the length of the hash and the limits to the non-suspicious changes that can be introduced, if the attacker can generate sufficient variations, then the chance of matching hash outputs can be better than 50%. This effectively means that a hash function that outputs 128-bit hashes can be attacked by a mechanism that can generate 2 64 variations. Computing 2 64 variations will take much less time than computing 2 128 variations.

Attacks that exploit collisions are difficult to launch, but the principle behind the attack informs the need to use authentication methods that use both strong ciphers and strong protocol and software implementations.