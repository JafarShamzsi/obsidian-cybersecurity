A network directory lists the subjects (principally users, computers, and services) and objects (such as directories and files) available on the network plus the permissions that subjects have over objects. A directory facilitates authentication and authorization, and it is critical that it be maintained as a highly secure service. Most directory services are based on the Lightweight Directory Access Protocol (LDAP), running over port 389. The basic protocol provides no security and all transmissions are in plaintext, making it vulnerable to sniffing and on-path attacks. Authentication (referred to as binding to the server) can be implemented in the following ways:

- **No Authentication**—means anonymous access is granted to the directory.
- **Simple Bind**—means the client must supply its distinguished name (DN) and password, but these are passed as plaintext.
- **Simple Authentication and Security Layer (SASL)**—means the client and server negotiate the use of a supported authentication mechanism, such as Kerberos. The STARTTLS command can be used to require encryption (sealing) and message integrity (signing). This is the preferred mechanism for Microsoft's Active Directory (AD) implementation of LDAP.
- LDAP Secure (LDAPS)—means the server is installed with a digital certificate, which it uses to set up a secure tunnel for the user credential exchange. LDAPS uses port 636.

If secure access is required, anonymous and simple authentication access methods should be disabled on the server.

Generally, two levels of access will need to be granted on the directory: read-only access (query) and read/write access (update). This is implemented using an access control policy, but the precise mechanism is vendor-specific and not specified by the LDAP standards documentation.

Unless hosting a public service, the LDAP directory server should only be accessible from the private network. This means that the LDAP port should be blocked by a firewall from access over the public interface. If there is integration with other services over the Internet, ideally only authorized IPs should be permitted.