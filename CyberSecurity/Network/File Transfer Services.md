There are many ways of transferring files across networks. A network operating system can host shared folders and files, enabling them to be copied or accessed over the local network or via remote access (over a VPN, for instance). Email and messaging apps can send files as attachments. HTTP supports file download (and uploads via various scripting mechanisms). There are also peer-to-peer file sharing services.

Despite the availability of these newer protocols and services, the File Transfer Protocol (FTP) remains very popular because it is efficient and has wide cross-platform support.

### File Transfer Protocol

A File Transfer Protocol (FTP) server is typically configured with several public directories, hosting files, and user accounts. Most HTTP servers also function as FTP servers, and FTP services, accounts, and directories may be installed and enabled by default when you install a web server. FTP is more efficient than file attachments or HTTP file transfer but has no security mechanisms. All authentication and data transfer are communicated as plaintext, meaning that credentials are easily picked out of intercepted FTP traffic.

You should check that users do not install unauthorized servers on their PCs (a rogue server). For example, a version of IIS that includes HTTP, FTP, and SMTP servers is shipped with client versions of Windows, though it is not installed by default.

### SSH FTP (SFTP) and FTP Over SSL (FTPS)

Secure File Transfer Protocol (SFTP) addresses privacy and integrity issues of FTP by encrypting the authentication and data transfer between client and server. In SFTP, a secure link is created between the client and server using Secure Shell (SSH) over TCP port 22. Ordinary FTP commands and data transfer can then be sent over the secure link without the risk of eavesdropping or on-path attacks. This solution requires an SSH server that supports SFTP and SFTP client software.

Another means of securing FTP is to use the connection security protocol SSL/TLS. There are two means of doing this:

- **Explicit TLS (FTPES)**—uses the AUTH TLS command to upgrade an unsecure connection established over port 21 to a secure one. This protects authentication credentials. The data connection for the file transfers can also be encrypted (using the PROT command).
- Implicit TLS (FTPS)—negotiates an SSL/TLS tunnel before the exchange of any FTP commands. This mode uses the secure port 990 for the control connection.

FTPS is tricky to configure when there are firewalls between the client and server. Consequently, FTPES is usually the preferred method.