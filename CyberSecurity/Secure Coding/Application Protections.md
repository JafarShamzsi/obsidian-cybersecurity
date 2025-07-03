Data exposure is a fault that allows privileged information (such as a token, password, or personal data) to be read without being subject to the appropriate access controls. Applications must only transmit such data between authenticated hosts, using cryptography to protect the session. When incorporating encryption in code, it is important to use industry standard encryption libraries that are proven to be strong, rather than internally developed ones.

### Error Handling

A well-written application must be able to handle errors and exceptions gracefully. This means that the application performs in a controlled way when something unpredictable happens. An error or exception could be caused by invalid user input, a loss of network connectivity, another server or process failing, and so on. Ideally, the programmer will have written a structured exception handler (SEH) to dictate what the application should then do. Each procedure can have multiple exception handlers.

Some handlers will deal with anticipated errors and exceptions; there should also be a catchall handler that will deal with the unexpected. The main goal must be for the application not to fail in a way that allows the attacker to execute code or perform some sort of injection attack. One infamous example of a poorly written exception handler is the Apple GoTo bug ([https://www.wired.com/2014/02/gotofail/](https://www.wired.com/2014/02/gotofail/)).

Another issue is that an application's interpreter may default to a standard handler and display default error messages when something goes wrong. These may reveal platform information and the inner workings of code to an attacker. It is better for an application to use custom error handlers so that the developer can choose the amount of information shown when an error is caused.

Technically, an error is a condition that the process cannot recover from, such as the system running out of memory. An exception is a type of error that can be handled by a block of code without the process crashing. Note that exceptions are still described as generating error codes/messages, however.

### Memory Management

Many arbitrary code attacks depend on the target application having faulty memory management procedures. This allows the attacker to execute their own code in the space marked out by the target application. There are known unsecure practices for memory management that should be avoided and checks for processing untrusted input, such as strings, to ensure that it cannot overwrite areas of memory.

### Client-Side vs. Server- Side Validation

A web application (or any other client-server application) can be designed to perform code execution and input validation locally (on the client) or remotely (on the server). An example of client-side execution is a document object model (DOM) script to render the page using dynamic elements from user input. Applications may use both techniques for different functions. The main issue with client-side validation is that the client will always be more vulnerable to some sort of malware interfering with the validation process. The main issue with server-side validation is that it can be time-consuming, as it may involve multiple transactions between the server and client. Consequently, client-side validation is usually restricted to informing the user that there is some sort of problem with the input before submitting it to the server. Even after passing client-side validation, the input will still undergo server-side validation before it can be posted (accepted). Relying on client-side validation only is poor programming practice.

### Application Security in the Cloud

Cloud hardening and application security are complementary capabilities designed to support the shared responsibility model in cloud environments where cloud service providers are responsible for securing the infrastructure and customers are responsible for securing their data and applications. Cloud hardening practices fortify the cloud infrastructure, reducing its attack surface, whereas application security ensures that software is designed, developed, and deployed securely. Together, these approaches create layered defenses that can counter many different types of threats.

Cloud hardening includes least privilege access policies to restrict users to the minimum permissions needed to perform their duties. Encryption protects data in transit and at rest. Regular audits and continuous monitoring practices identify potential security risks, and regular vulnerability assessments and penetration testing detect and address any potential security issues or misconfigurations.

### Monitoring Capabilities

Secure coding practices focus primarily on preventing software vulnerabilities but also stress enhancements to logging and monitoring capabilities. These features support security analysts tasked with detecting potential threats and malicious activity in software. Writing code with enhanced monitoring capabilities improves the granularity and effectiveness of logging and alerting systems, which are crucial system monitoring tools.

Implementing comprehensive and meaningful logging requires developers to ensure their applications generate logs that capture important events and activities to support security audits, incident response, and system troubleshooting. Secure coding practices encourage robust error handling to hide or mask sensitive debugging information, and this practice minimizes the risk of attackers exploiting information displayed in error messages. Integrating real-time alerting capabilities within the application code can significantly improve threat detection. For example, code that triggers alerts when specific events occur, such as repeated failed login attempts or unusual data transfers, helps security analysts monitor applications more effectively. These alerts often indicate a potential security breach and provide crucial information for incident response teams.