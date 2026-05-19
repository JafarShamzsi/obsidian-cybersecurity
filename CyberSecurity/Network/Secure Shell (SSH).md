**Secure Shell (SSH)** is a cryptographic network protocol used for secure remote access to command-line terminals and for encrypted file transfer.

- **Primary uses**:
  - Secure remote administration
  - Encrypted file transfers (via SCP or SFTP)
  - Secure tunneling

- **Default Port**: TCP 22
- **Most common implementation**: OpenSSH (https://openssh.com)

---

## SSH Architecture

SSH operates on a **client-server model** and uses a combination of:
- **Symmetric encryption** (established after handshake)
- **Asymmetric encryption** (for host verification and optionally client authentication)
- **Hashing** (message integrity)

### SSH Session Establishment
1. Client initiates connection to server.
2. Server presents its **host key** (public key) to prove identity.
3. A secure channel is established using **Diffie-Hellman key exchange** or a similar method.
4. Client sends **authentication credentials**.
5. If successful, an interactive shell is opened over the encrypted session.
![[4777-1692974866308.png]]
---

## Host Key Verification

- The SSH server is identified by its **host key pair** (public/private).
- On first connection, the client typically displays a **host key fingerprint** warning:
  > “The server's host key was not found in the cache...”

- User has options:
  - **Yes**: Trust and cache the host key (recommended only if key is verified out-of-band)
  - **No**: Connect without caching key (not recommended)
  - **Cancel**: Abort connection

> **Security Note**: If the host key changes unexpectedly, it may indicate a **Man-in-the-Middle (MitM) attack**. Only proceed after verifying the host.

---

## SSH Client Authentication Methods

The SSH server uses the `sshd_config` file (`/etc/ssh/sshd_config`) to control which authentication methods are allowed:

### 1. **Username/Password**
- Basic method; credentials verified against local users or RADIUS server.
- Least secure; **vulnerable to brute-force attacks**.
- Should always be paired with **fail2ban**, rate-limiting, and/or **MFA**.

### 2. **Public Key Authentication**
- Recommended method for automation and administrative access.
- Each user has:
  - **Private key** (securely stored on client)
  - **Public key** (stored in `~/.ssh/authorized_keys` on the server)

- Process:
  1. Client proves possession of private key.
  2. Server matches it against the authorized public keys.
- Supports **password-less** and **non-interactive login**.

### 3. **Kerberos / GSSAPI**
- Enterprise single sign-on integration using Kerberos.
- Useful in **Active Directory (AD)** environments.
- Client presents a **Ticket Granting Ticket (TGT)** to the server.
- Validated via a **domain controller**.

---

## SSH Key Management

- **Host key**: Unique identity of SSH server.
- **User key**: Identity used by SSH clients.

> **Key Management Best Practices**:
- Rotate keys regularly.
- Delete public keys immediately upon user deprovisioning.
- Monitor for **unauthorized public keys**.
- If a private key is suspected to be compromised:
  - Remove corresponding public key from the server.
  - Regenerate key pair and redistribute securely.

---

## Key Generation and Deployment

### Generate Key Pair (Client):
```bash
ssh-keygen -t rsa
```

## Copy Public Key to Server:
```
ssh-copy-id bobby@10.1.0.10
```

- Adds public key to `~/.ssh/authorized_keys` on server.
### Manual Deployment:

- Append public key to:
```
~/.ssh/authorized_keys
```
## File Transfers with SSH

### Secure Copy (SCP)

- Copy from remote → local:
```
scp bobby@10.1.0.10:/logs/audit.log audit.log
```
- Copy from local → remote:
```
scp audit.log bobby@10.1.0.10:/logs/
```
- Copy a directory recursively:
```
scp -r ./localdir bobby@10.1.0.10:/backup/
```

### Secure File Transfer Protocol (SFTP)

- Interactive command set for navigating and transferring files:
```
sftp bobby@10.1.0.10
```

## SSH Security Best Practices

| Practice                    | Description                                        |
| --------------------------- | -------------------------------------------------- |
| **Disable root login**      | Prevent `PermitRootLogin yes`; use `sudo`          |
| **Enforce public key auth** | Set `PasswordAuthentication no`                    |
| **Use strong key types**    | Prefer `ed25519` or `rsa 4096`                     |
| **Restrict users**          | Use `AllowUsers` or `AllowGroups`                  |
| **Enable logging**          | Audit login attempts and key usage                 |
| **Use Fail2Ban**            | Block brute-force attacks dynamically              |
| **Change default port**     | Obscurity isn’t security, but can reduce bot scans |