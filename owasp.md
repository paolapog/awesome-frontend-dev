The Open Web Application Security Project (OWASP) is a nonprofit foundation that works to improve the security of software. One of their most well-known projects is the OWASP Top 10, a standard awareness document for developers and web application security. It represents a broad consensus about the most critical security risks to web applications.

Here are the OWASP Top 10 Security Risks as of the latest edition (2021):

1. **Broken Access Control:** Restrictions on what authenticated users are allowed to do are often not properly enforced. Attackers can exploit these flaws to access unauthorized functionality and/or data, such as accessing other users' accounts, viewing sensitive files, modifying other users’ data, changing access rights, etc.

2. **Cryptographic Failures:** This is a new category for 2021, and it includes everything from not encrypting sensitive data, not validating or incorrectly validating encryption, to weak encryption that can be easily broken.

3. **Injection:** Injection flaws, such as SQL, NoSQL, OS, and LDAP injection, occur when untrusted data is sent to an interpreter as part of a command or query. The attacker’s hostile data can trick the interpreter into executing unintended commands or accessing data without proper authorization.

4. **Insecure Design:** This is another new category for 2021. It's a broad category that includes risks related to design principles like defense in depth, least privilege, least common mechanism, secure defaults, and others.

5. **Security Misconfiguration:** Security misconfiguration is the most commonly seen issue. This is commonly a result of insecure default configurations, incomplete or ad hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information.

6. **Vulnerable and Outdated Components:** Components, such as libraries, frameworks, and other software modules, run with the same privileges as the application. If a vulnerable component is exploited, such an attack can facilitate serious data loss or server takeover.

7. **Identification and Authentication Failures:** Application functions related to authentication and session management are often implemented incorrectly, allowing attackers to compromise passwords, keys, session tokens, or exploit other implementation flaws to assume other users' identities.

8. **Software and Data Integrity Failures:** This is a new category for 2021. It includes risks related to the integrity of software and data, and how failures can lead to unauthorized changes.

9. **Security Logging and Monitoring Failures:** Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain persistence, pivot to more systems to tamper with, extract, or destroy data.

10. **Server-Side Request Forgery (SSRF):** This is a new category for 2021. It involves an attacker abusing functionality on the server to read or update internal resources.

Each of these risks is not standalone but often found in combination with others. The OWASP Top 10 is a great starting point for organizations and developers to ensure that they are protecting against the most common and impactful risks.