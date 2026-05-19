The security considerations for new programming technologies should be well understood and tested before deployment. One of the challenges of application development is that the pressure to release a solution often trumps any requirement to ensure that the application is secure. A legacy software design process might be heavily focused on highly visible elements, such as functionality, performance, and cost. Modern development practices use a security development lifecycle running in parallel or integrated with the focus on software functionality and usability. Examples include Microsoft's SDL ([microsoft.com/en-us/securityengineering/sdl](https://www.microsoft.com/en-us/securityengineering/sdl)) and the OWASP Software Assurance Maturity Model ([owasp.org/www-project-samm](https://owasp.org/www-project-samm/)) and Security Knowledge Framework ([https://owasp.org/projects/spotlight/historical/2021.02.03/](https://owasp.org/projects/spotlight/historical/2021.02.03/)). OWASP also collates descriptions of specific vulnerabilities, exploits, and mitigation techniques, such as the OWASP Top 10 ([owasp.org/www-project-top-ten](https://owasp.org/www-project-top-ten/)).

### Input Validation

Input validation is an essential protection technique used in software and web development that addresses the issue of untrusted input. Untrusted input describes how an attacker can provide specially crafted data to an application to manipulate its behavior. Injection attacks exploit the input mechanisms applications rely on to execute malicious commands and scripts to access sensitive data, control the operation of the application, gain access to otherwise protected back-end systems, and disrupt operations.

OWASP provides an excellent overview of input validation at [https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html) .

Without effective input validation, applications are vulnerable to many different classes of injection attacks, such as SQL injection, code injection, cross-site scripting (XSS), and many others.

 
|Validation Method|Description|
|---|---|
|Allowlisting|This method only permits inputs that match a predetermined and approved set of values or patterns.|
|Blocklisting|This approach explicitly blocks known harmful inputs, such as certain special characters or patterns commonly used in attacks.|
|Data Type Checks|These checks ensure the input data is of the expected type, such as a string, integer, or date.|
|Range Checks|These validate that numeric inputs fall within expected ranges.|
|Regular Expressions|Also known as regex, these are used to match input to expected patterns or signs of malicious activity.|
|Encoding|This helps to safely and reliably prevent special characters in input from being interpreted as executable commands or scripts.|

### Secure Cookies

Cookies are small pieces of data stored on a computer by a web browser while accessing a website. They maintain session states, remember user preferences, and track user behavior and other settings. Cookies can be exploited if not properly secured, leading to attacks such as session hijacking or cross-site scripting.

To implement secure cookies, developers must follow certain well-documented principles, such as using the 'Secure' attribute for all cookies to ensure they are only sent over HTTPS connections and protected from interception via eavesdropping, using the 'HttpOnly' attribute to prevent client-side scripts from accessing cookies and protect against cross-site scripting attacks, and using the 'SameSite' attribute to limit when cookies are sent to mitigate cross-site request forgery attacks. Additionally, cookies should have expiration time limits to restrict their usable life.

Secure cookie techniques are critical in mitigating several web-based application attacks, particularly those focused on unauthorized access or manipulation of session cookies. Developers can defend against attacks that target them by employing specific attributes within cookies.

### Static Code Analysis

Static code analysis is a crucial software development practice. It involves scrutinizing source code to identify potential vulnerabilities, errors, and noncompliant coding practices before the program is finalized. By examining code in a 'static' state, developers can catch and rectify issues early in the development lifecycle, making it a proactive approach to building secure, reliable, and high-quality software.

Application security approaches focus on software development and deployment lifecycles, with a heavy emphasis on secure coding practices that encourage developers to write code that prevents common vulnerabilities like SQL injection and cross-site scripting. Application security practices also mandate static application security testing (SAST) and dynamic application security testing (DAST). Coding practices designed to support regular patching and updates are crucial to support the prompt resolution of newly discovered vulnerabilities.

Static code analysis supports secure coding and is performed using specialized tools, often integrated into software development suites. These tools automate code checks against pre-determined rules and flag potential issues so developers can review and address them. Some commonly used static analysis tools include SonarQube ([https://www.sonarsource.com/products/sonarqube/](https://www.sonarsource.com/products/sonarqube/)), Coverity ([https://www.synopsys.com/software-integrity/security-testing/static-analysis-sast.html](https://www.synopsys.com/software-integrity/security-testing/static-analysis-sast.html)), and Fortify (https://www.opentext.com/products/fortify-static-code-analyzer).

Code signing practices use digital signatures to verify the integrity and authenticity of software code. Code signing serves a dual purpose: ensuring that software has not been tampered with since signing and confirming the software publisher's identity.

When software is digitally signed, the signer uses a private key to encrypt a hash or digest of the code—this encrypted hash and the signer's identity form the digital signature. Code signing requires using a certificate issued by a trusted certificate authority (CA). The certificate contains information about the signer's identity and is critical for verifying the digital signature. If the certificate is valid and issued by a trusted CA, the software publisher's identity can be confidently verified. Code signing helps analysts and administrators block untrusted software and also helps protect software publishers by providing a mechanism to validate the authenticity of their code. Overall, code signing helps build trust in the software distribution process.

While code signing provides assurance about the origin of code and verifies code integrity, it does not inherently assure the safety or security of the code itself. Code signing certifies the source and integrity of the code, but it doesn't evaluate the quality or security of the code. The signed code could still contain bugs, vulnerabilities, or malicious code inserted by the original author. Signing ensures software is from the expected developer and in the state the developer intended. While code signing adds trust and authenticity to software distribution, it should not be relied upon to guarantee secure or bug-free code.

![A Screengrab shows three overlapping windows titled, Bitwarden installer, digital signature details, and certificate.](https://s3.amazonaws.com/wmx-api-production/courses/54332/images/1711-1692974872050.png) Description

The first window is titled, Bitwarden-Installer hyphen 2022 point 10 point 1 properties. Digital signatures tab is selected. A section titled, signature list provides details of name of signer, digest algorithm, and timestamp.

The second window is titled, digital signature details. General tab is selected. The tab lists the signer information and counter signatures.  The third window is titled, Certificate. General tab is selected. It provides certificate information. Install certificate and issuer statement buttons are present on the bottom right. Below the two buttons is an OK button.

Reviewing the digital signature contained within the Bitwarden Password Management app installer.