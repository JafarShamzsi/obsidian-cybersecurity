Attacks such as session replay, CSRF, and most types of XSS are client-side attacks. This means that they execute arbitrary code on the browser. A server-side attack causes the server to do some processing or run a script or query in a way that is not authorized by the application design. Most server-side attacks depend on some kind of injection attack.

An injection attack exploits some unsecure way in which the application processes requests and queries. For example, an application might allow a user to view their profile with a database query that should return the single record for that one user's profile. An application vulnerable to an injection attack might allow a threat actor to return the records for all users, or to change fields in the record when they are only supposed to be able to read them.

The persistent XSS and abuse of SQL queries and parameters discussed earlier in the course are both types of injection attack. There are a number of other injection attack types that pose serious threats to web applications and infrastructure.

### Extensible Markup Language Injection

Extensible Markup Language (XML) is used by apps for authentication and authorizations, and for other types of data exchange and uploading. Data submitted via XML with no encryption or input validation is vulnerable to spoofing, request forgery, and injection of arbitrary data or code. For example, an XML External Entity (XXE) attack embeds a request for a local resource:

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE foo [<!ELEMENT foo ANY ><!ENTITY bar SYSTEM "file:///etc/config"> ]>

<bar>&bar;</bar>

This defines an entity named bar that refers to a local file path. A successful attack will return the contents of /etc/config as part of the response.

### Lightweight Directory Access Protocol (LDAP) Injection

The Lightweight Directory Access Protocol (LDAP) is another example of a query language. LDAP is specifically used to read and write network directory databases. A threat actor could exploit either unauthenticated access or a vulnerability in a client app to submit arbitrary LDAP queries. This could allow accounts to be created or deleted, or for the attacker to change authorizations and privileges.

LDAP filters are constructed from (name=value) attribute pairs delimited by parentheses and the logical operators AND (&) and OR (|). Adding filter parameters as unsanitized input can bypass access controls. For example, if a web form authenticates to an LDAP directory with the valid credentials Bob and Pa$$w0rd , it may construct a query such as this from the user input:

(&(username=Bob)(password=Pa$$w0rd))

Both parameters must be true for the login to be accepted. If the form input is not sanitized, a threat actor could bypass the password check by entering a valid username plus an LDAP filter string, such as **bob)(&))** . This causes the password filter to be dropped for a condition that is always true:

(&(username=Bob)(&))