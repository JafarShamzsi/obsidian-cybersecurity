Email services use two types of protocols:

- The Simple Mail Transfer Protocol (SMTP) specifies how mail is sent from one system to another.
- A mailbox protocol stores messages for users and allows them to download them to client computers or manage them on the server.

### Secure SMTP (SMTPS)

To deliver a message, the SMTP server of the sender discovers the IP address of the recipient SMTP server using the domain name part of the email address. The SMTP server for the domain is registered in DNS using a mail exchanger (MX) record.

SMTP communications can be secured using TLS. This works much like HTTPS with a certificate on the SMTP server. There are two ways for SMTP to use TLS:

- **STARTTLS**—is a command that upgrades an existing unsecure connection to use TLS. This is also referred to as explicit TLS or opportunistic TLS.
- **SMTPS**—establishes the secure connection before any SMTP commands (HELO, for instance) are exchanged. This is also referred to as implicit TLS.

The STARTTLS method is generally more widely implemented than SMTPS. Typical SMTP configurations use the following ports and secure services:

- **Port 25**—is used for message relay (between SMTP servers or message transfer agents [MTA]). If security is required and supported by both servers, the STARTTLS command can be used to set up the secure connection.
- **Port 587**—is used by mail clients ( message submission agents [MSA]) to submit messages for delivery by an SMTP server. Servers configured to support port 587 should use STARTTLS and require authentication before message submission.
- **Port 465**—is used by some providers and mail clients for message submission over implicit TLS (SMTPS), though this usage is now deprecated by standards documentation.

### Secure POP (POP3S)

The Post Office Protocol v3 (POP3) is a mailbox protocol designed to store the messages delivered by SMTP on a server. When the client connects to the mailbox, POP3 downloads the messages to the recipient's email client.

![A Screengrab shows few lines of code to configure mailbox access protocols on a server.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/6920-1692974871372.png)

Configuring mailbox access protocols on a server.

A POP3 client application, such as Microsoft Outlook or Mozilla Thunderbird, establishes a TCP connection to the POP3 server over port 110. The user is authenticated (by username and password), and the contents of their mailbox are downloaded for processing on the local PC. POP3S is the secured version of the protocol operating over TCP port 995 by default.

### Secure IMAP (IMAPS)

Compared to POP3, the Internet Message Access Protocol (IMAP) supports permanent connections to a server and connects multiple clients to the same mailbox simultaneously. It also allows a client to manage mail folders on the server. Clients connect to IMAP over TCP port 143. They authenticate themselves , then retrieve messages from the designated folders. Like other email protocols, the connection can be secured by establishing an SSL/TLS tunnel. The default port for IMAPS is TCP port 993.