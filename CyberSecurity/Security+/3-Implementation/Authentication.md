# Authentication in Cybersecurity  

## Overview  
**Authentication** is the process of **verifying the identity** of a subject (user, device, or process) before granting access to a system or resource. It ensures that only **legitimate users or systems** can interact with protected data, preventing unauthorized access.  

Authentication is the second step in the **AAA model** (**Authentication, Authorization, and Accounting**), following **identification** and preceding **authorization**.

## **1. How Authentication Works**  
- A **subject** (user, device, or process) provides credentials.  
- The system **verifies** the credentials against a database or authentication server.  
- If the credentials match, **access is granted**; otherwise, access is denied.  

**Example:**  
- A **user enters a username and password** → (Identification)  
- The system **validates the credentials** against a stored record → (Authentication)  
- The system **checks permissions and grants access** → (Authorization)  

## **2. Types of Authentication**  

| **Type** | **Description** | **Example Methods** |
|----------|---------------|----------------------|
| **Single-Factor Authentication (SFA)** | Requires only one authentication factor. | Passwords, PINs |
| **Multi-Factor Authentication (MFA)** | Requires two or more authentication factors. | Password + OTP, Fingerprint + Smart Card |
| **Two-Factor Authentication (2FA)** | A subset of MFA using exactly two factors. | ATM Card + PIN |
| **Passwordless Authentication** | Uses non-password methods. | Biometrics, Security Tokens |
| **Continuous Authentication** | Verifies identity throughout the session. | AI-based behavior analysis |

## **3. Authentication Factors**  

| **Factor Type** | **Description** | **Examples** |
|---------------|---------------|-------------|
| **Something You Know** | Information only the user knows. | Password, PIN, Security Question |
| **Something You Have** | A physical device or token. | Smart Card, OTP, Security Key |
| **Something You Are** | Biometric characteristics. | Fingerprint, Face ID, Retina Scan |
| **Somewhere You Are** | Location-based authentication. | IP Address, GPS Location |
| **Something You Do** | Behavioral authentication. | Typing speed, Mouse movements |

## **4. Authentication Protocols**  

| **Protocol** | **Description** | **Common Uses** |
|-------------|---------------|----------------|
| **LDAP (Lightweight Directory Access Protocol)** | Manages user authentication in directories. | Enterprise networks (Active Directory) |
| **Kerberos** | Uses ticket-based authentication. | Secure enterprise authentication (Windows AD) |
| **OAuth 2.0** | Delegates authentication to an identity provider. | Web & API authentication (Google Login) |
| **SAML (Security Assertion Markup Language)** | Federated authentication using XML. | Single Sign-On (SSO) for enterprises |
| **OpenID Connect (OIDC)** | Extends OAuth 2.0 for authentication. | Web authentication (Google, Facebook login) |
| **RADIUS (Remote Authentication Dial-In User Service)** | Centralized authentication for remote access. | VPNs, Wi-Fi authentication |

## **5. Password Security & Best Practices**  
- **Use Strong Passwords** → Minimum 12-16 characters with a mix of upper/lowercase, numbers, and symbols.  
- **Implement Multi-Factor Authentication (MFA)** → Prevents unauthorized access even if a password is compromised.  
- **Enforce Password Rotation Policies** → Periodically change passwords to reduce risks.  
- **Use Password Managers** → Securely store and generate complex passwords.  
- **Salting & Hashing** → Store passwords securely using hashing algorithms like **bcrypt, PBKDF2, or Argon2**.  

## **6. Authentication Attacks & Mitigations**  

| **Attack Type** | **Description** | **Mitigation** |
|---------------|---------------|----------------|
| **Brute Force Attack** | Repeatedly guessing passwords. | Enforce account lockout, rate limiting, strong passwords. |
| **Credential Stuffing** | Using leaked credentials from breaches. | Require unique passwords, enable MFA. |
| **Phishing** | Trick users into revealing credentials. | Educate users, use anti-phishing tools. |
| **Man-in-the-Middle (MitM)** | Intercepting authentication data in transit. | Use TLS encryption, implement MFA. |
| **Session Hijacking** | Stealing active session tokens. | Implement secure cookies, use HTTP-only and Secure flags. |

## **7. Real-World Applications**  
1. **Corporate Security** → Employees authenticate via **Active Directory & SSO**.  
2. **Banking & Finance** → Customers authenticate with **MFA & biometric verification**.  
3. **Cloud Services** → Users authenticate via **OAuth 2.0 & OpenID Connect**.  
4. **IoT Devices** → Devices authenticate via **certificates & device fingerprints**.  

## **8. Exam Tips**  
- **Authentication verifies identity, while authorization determines access.**  
- **MFA is more secure than SFA and should always be implemented where possible.**  
- **OAuth 2.0 is used for API authentication, while Kerberos is used for enterprise logins.**  
- **Passwordless authentication is gaining popularity in modern security solutions.**  
- **Salting & hashing prevent password storage vulnerabilities.**  

## **Related Topics**  
- [[3-Implementation/Authorization in Cybersecurity]]  
- [[3-Implementation/Access Control Models]]  
- [[4-Operations-Incident-Response/Logging and Monitoring]]  
- [[Glossary#Authentication]]  

## **Practice Questions**  
1. **Which of the following is NOT an authentication factor?**  
   - A. Something You Know  
   - B. Something You Have  
   - C. Something You Are  
   - D. Something You Own  
   - **Answer:** D. Something You Own (not a standard factor).  

2. **Which authentication protocol is commonly used for Single Sign-On (SSO)?**  
   - A. LDAP  
   - B. Kerberos  
   - C. OAuth 2.0  
   - D. SAML  
   - **Answer:** D. SAML (Security Assertion Markup Language).  

3. **What is the main purpose of Multi-Factor Authentication (MFA)?**  
   - A. To eliminate passwords  
   - B. To make authentication faster  
   - C. To require multiple methods of identity verification  
   - D. To store passwords securely  
   - **Answer:** C. To require multiple methods of identity verification.  


---
