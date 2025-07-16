Directory traversal is another type of injection attack performed against a web server. The threat actor submits a request for a file outside the web server's root directory by submitting a path to navigate to the parent directory ( ../ ). This attack can succeed if the input is not filtered properly, and access permissions on the file allow the web server's process to read, write, or execute it.

The threat actor might use a canonicalization attack to disguise the nature of the malicious input. Canonicalization refers to the way the server converts between the different methods by which a resource may be represented and submitted to the simplest (or canonical) method used by the server to process the input. Examples of encoding schemes include HTML entities and character set percent encoding. An attacker might be able to exploit vulnerabilities in the canonicalization process to perform code injection or facilitate directory traversal. For example, to perform a directory traversal attack, the attacker might submit a URL such as the following :

http://victim.foo/?show=../../../../etc/config

A limited input validation routine would prevent the use of the string ../ and refuse the request. If the attacker submitted the URL using the encoded version of the characters, they might be able to circumvent the validation routine:

http://victim.foo/?show=%2e%2e%2f%2e%2e%2f%2e%2e%2f%2e%2e%2fetc/config

A command injection attack attempts to cause the server to run OS shell commands and return the output to the browser. As with directory traversal, the web server should normally be able to prevent commands from operating outside of the server's directory root and to prevent commands from running with any privilege level other than the web server's "guest" user (which is normally granted only very restricted privileges). A successful command injection attack would find some way of circumventing this security, or exploit a web server that is not properly configured.
