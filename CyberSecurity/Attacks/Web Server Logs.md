Web servers are typically configured to log HTTP traffic that encounters an error or traffic that matches some predefined rule set. This can preserve indicators of attempted and successful replay, forgery, and injection attacks.

The status code of a response can reveal quite a bit about both the request and the server's behavior. Codes in the 400 range indicate client-based errors, while codes in the 500 range indicate server-based errors. For example, repeated 403 ("Forbidden") responses may indicate that the server is rejecting a client's attempts to access resources they are not authorized to. A 502 ("Bad Gateway") response could indicate that communications between the target server and its upstream server are being blocked, or that the upstream server is down.

In addition to status codes, some web server software also logs HTTP header information for both requests and responses. This can provide a detailed picture of the makeup of each request or response, such as cookie information.

![](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/7907-1692974876054.png)

Web server access log showing an ordinary client (203.0.113.66) accessing a page and its associated image resources, and then scanning activity from the Nikto app running on 203.0.113.66. The scanning activity generates multiple 404 errors as it tries to map the web app's attack surface by enumerating common directories and files.