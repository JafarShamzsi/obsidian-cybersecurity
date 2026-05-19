In contrast with replay attacks, a **forgery attack** hijacks an authenticated session to perform some action without the user's consent.

### Cross-Site Request Forgery

A cross-site request forgery (CSRF) can exploit applications that use cookies to authenticate users and track sessions. To work, the threat actor must convince the victim to start a session with the target site. The attacker must then pass an HTTP request to the victim's browser that spoofs an action on the target site, such as changing a password or an email address. This request could be disguised in ways that accomplish the attack without the victim necessarily having to click a link. If the target site assumes that the browser is authenticated because there is a valid session cookie, and doesn't complete any additional authorization process on the attacker's input, it will accept the request as genuine. This is also referred to as a confused deputy attack.
![[Pasted image 20250716173551.png]]
Description

The steps are as follows:

1. Alice signs in at a trusted site.

2. Mallory sends Alice a malicious link.

3. Alice trusts the link and clicks it while still logged in to the trusted site.

4. The link makes a malicious request on the site.

Cross-site request forgery example. (Images © 123RF.com.)

### Server-Side Request Forgery

A server-side request forgery (SSRF) causes a server application to process an arbitrary request that targets another service. The target service could be another application running on the same host or a service running on a remote host. SSRF exploits both the lack of authentication between the internal servers and services. It also relies on weak input validation, which allows the attacker to submit arbitrary requests.

SSRF attacks are often targeted against cloud infrastructure where the web server is only the public-facing component of a deeper processing chain. A typical web application comprises multiple layers of servers, with a client interface, middleware logic layers, and a database layer. Requests initiated from the client interface (a web form) are likely to require multiple requests and responses between the middleware and back-end servers. These will be implemented as HTTP header requests and responses between each server. SSRF is a means of accessing these internal servers by causing the public server to execute requests on them. While with CSRF an exploit only has the privileges of the client, with SSRF the manipulated request is made with the server's privilege level.
![[Pasted image 20250716173559.png]]
Description

The steps are as follows:

1. Mallory cannot access the database server directly.

2. Mallory crafts a malicious request and submits it to the front-end server.

3. The web server performs the malicious request.

4. The database server accepts the request because it appears to come from the web server.

5. Mallory may also be get information from the internal server.

Server-side request forgery example. (Images © 123RF.com.)
