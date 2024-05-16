# 1 OWASP TOP 10
The OWASP Top 10 is a standard awareness document for developers and web application security. It represents a broad consensus about the most critical security risks to web applications.

## 1.1 Broken Access Control
### 1.1.1 Description
94% of applications were tested for some form of broken access control
### 1.1.2 Scenario
An application uses unpurified input in an SQL call that is accessing account information: *pstmt.setString(1, request.getParameter("acct"));*
*ResultSet results = pstmt.executeQuery( );*
An attacker simply modifies the browser's 'acct' parameter to send whatever account number they want. If not correctly verified, the attacker can access any user's account.
### 1.1.3 Mitigation
- Proper access control 
- Indirect reference maps 
- Input validation

## 1.2 Cryptographic failures
### 1.2.1 Description
Sensitive data exposure or system compromise
### 1.2.2 Scenario
**Cloudbleed**
An application encrypts credit card numbers in a database using automatic database encryption, but this data is automatically decrypted when retrieved, allowing an SQL injection flaw to retrieve credit card numbers in clear text
https://en.wikipedia.org/wiki/Cloudbleed
### 1.2.3 Mitigation
- Verify your architecture 
	- Identify all sensitive data 
	- Identify all the places that data is stored 
	- Ensure threat model accounts for possible attacks 
	- Use encryption to counter the threats, don’t just ‘encrypt’ the data 
- Store passwords using strong adaptive and salted hashing functions with a work factor (delay factor)
- Protect with appropriate mechanisms for example file encryption
- Don't use broken cryptography
- Verify the implementation

## 1.3 Injection
### 1.3.1 Description
94% of the applications were tested for some form of injection
### 1.3.2 Types
- SQL injections 
- Cross-site Scripting
- LDAP, XPath statements 
- XML and SOAP 
- Operating System commands (Shell Injection) 
- E-mail services / SMTP
### 1.3.3 Mitigation
Sanitize and validate ALL user inputs.

## 1.4 Insecure design
### 1.4.1 Description
"New" category added in 2022

### 1.4.2 Scenario
A movie theatre chain that allows group booking discounts requires a deposit for groups of more than fifteen people. Attackers threat model this flow to see if they can book hundreds of seats across various theatres in the chain, thereby causing thousands of dollars in lost income
### 1.4.3 Mitigation
- Establish and use a [[secure development lifecycle]] with AppSec professionals to help evaluate and design security and privacy-related controls 
- Establish and use a library of secure design patterns or paved-road, ready-to-use components 
- Use threat modelling for critical authentication, access control, business logic, and key flows 
- Integrate security language and controls into user stories 
- Integrate plausibility checks at each tier of your application
- Write unit and integration tests to validate that all critical flows are resistant to the threat model.
- Segregate tier layers on the system and network layers depending on the exposure and protection needs 
- Limit resource consumption by user or service

## 1.5 Security Misconfiguration
### 1.5.1 Scenario
The application server comes with sample applications not removed from the production server. These sample applications have known security flaws attackers use to compromise the server. Suppose one of these applications is the admin console, and default accounts weren't changed. In that case, the attacker logs in with default passwords and takes over
### 1.5.2 Mitigation
- Keep underlying software and systems up to date 
- Use generic error messages 
- Do not deploy hidden (admin) accounts or testing functionality 
- Security sensitive and confidential information should not be cached 
- Autocomplete should be disabled for security logins and sensitive information 
- Set tight cookie domain 
- Set httpOnly
- Harden systems 
	- e.g. remove default accounts and ports that are not needed
	- systems in DMZ (demilitarized zone, a perimeter network that protects and adds an extra layer of security to an organization's internal local-area network from untrusted traffic.) require a stricter hardening 


## 1.6 Vulnerable and Outdated Components
### 1.6.1 Description
Vulnerable and Outdated Components means that your application is using components with known security vulnerabilities or components that are not up to date with the latest security patches. This includes:
1. Outdated Libraries and Framework: Using old versions of libraries and frameworks that have known vulnerabilities.
2. Unpatched Software: Components that haven't been updated with the latest security patches.
3. Unsupported Software: Using software that is no longer maintained or supported by the vendor, which means no future security updates.
### 1.6.2 Scenario
1. JavaScript Libraries: Using an old version of jQuery with known XSS vulnerabilities.
2. Server-Side Frameworks: Running a web application on an outdated version of a web server like Apache or Nginx with known exploits.
3. Dependency Management: Including dependencies in your project that have known vulnerabilities, such as older versions of the Spring framework or Apache Struts.
### 1.6.3 Mitigation
#### 1.6.3.1 Remove Unnecessary Elements
- Eliminate unused dependencies, unnecessary features, components, files, and documentation to reduce the attack surface.
#### 1.6.3.2 Maintain an Updated Inventory
- Continuously track the versions of both client-side and server-side components, including their dependencies.
- Use tools like OWASP Dependency Check, retire.js, and others to automate this process.
- Regularly check sources like the Common Vulnerability and Exposures (CVE) and National Vulnerability Database (NVD) for known vulnerabilities.
#### 1.6.3.3 Use Secure Sources
- Only download components from official sources.
- Ensure that these components are obtained over secure links to prevent tampering.
#### 1.6.3.4 Monitor Component Health
- Keep an eye on libraries and components to ensure they are actively maintained and receive regular security patches.
- If a component cannot be patched, consider using a virtual patch to monitor, detect, or protect against vulnerabilities.
#### 1.6.3.5 Special Considerations for IoT Devices
- Patching IoT devices can be challenging, but it is crucial, especially for critical devices like biomedical equipment.
- Prioritize patching these devices to maintain their security.
#### 1.6.3.6 Ongoing Maintenance Plan
- Develop and implement a plan for continuously monitoring, triaging, and applying updates or configuration changes throughout the application's or portfolio's lifetime.


## 1.7 Identification and Authentication failures
### 1.7.1 Scenario
Most authentication attacks occur due to the continued use of passwords as a sole factor. Once considered the best practices, password rotation and complexity requirements encourage users to use and reuse weak passwords. Organizations are recommended to stop these practices per [[#2 NIST 800 63]] and use multi-factor authentication

### 1.7.2 Mitigation
- Where possible, implement multi-factor authentication to prevent automated credential stuffing, brute force, and stolen credential reuse attacks 
- Do not ship or deploy with any default credentials, particularly for admin users 
- Implement password checks, such as testing new or changed passwords against the top 10,000 worst passwords list. 
- Align password length, complexity, and rotation policies with National Institute of Standards and Technology [[#2 NIST 800 63]]
- Ensure registration, credential recovery, and API pathways are hardened against account enumeration attacks by using the same messages for all outcomes. 
- Limit or increasingly delay failed login attempts but be careful not to create a denial-of-service scenario. Log all failures and alert administrators when credential stuffing, brute force, or other attacks are detected. 
- Use a server-side, secure, built-in session manager that generates a new random session ID with high entropy after login. Session identifier should not be in the URL, be securely stored, and invalidated after logout, idle, and absolute timeouts



## 1.8 Software and Data Integrity Failures
### 1.8.1 Scenario
Nation-states have been known to attack update mechanisms, with a recent notable attack being the SolarWinds Orion attack. The company that develops the software had secure build and update integrity processes. Still, these were able to be subverted, and for several months, the firm distributed a highly targeted malicious update to more than 18,000 organizations, of which around 100 or so— including a hospital—were affected. This is one of the most far-reaching and most significant breaches of this nature in history.

### 1.8.2 Mitigation
- Use digital signatures to verify the software or data is from the expected source and has not been altered. 
- Ensure libraries and dependencies, such as npm or Maven, are consuming trusted repositories. If you have a higher risk profile, consider hosting an internal repository.
- Ensure that a software supply chain security tool, such as OWASP Dependency Check or OWASP CycloneDX, is used to verify that components do not contain known vulnerabilities. 
- Ensure that there is a review process for code and configuration changes to minimize the chance that malicious code or configuration could be introduced into your software pipeline. 
- Ensure that your continuous integration and continuous deployment (CI/CD) pipeline has proper segregation, configuration, and access control to ensure the integrity of the code flowing through the build and deploy processes. 
- Ensure that unsigned or unencrypted serialized data is not sent to untrusted clients without some form of integrity check or digital signature to detect tampering or replay of the serialized data


## 1.9 Security Logging and Monitoring failures
### 1.9.1 Scenario
A children’s Health plan provider's website operator couldn't detect a breach due to a lack of monitoring and logging, the data breach could have been in progress since 2013, a period of more than seven years.

### 1.9.2 Mitigation
- Ensure all login, access control, and server-side input validation failures can be logged with sufficient user context to identify suspicious or malicious accounts
- Ensure log data is encoded correctly to prevent injections or attacks on the logging or monitoring systems 
- Ensure high-value transactions have an audit trail with integrity controls to prevent tampering or deletion, such as append-only database tables or similar 
- DevSecOps teams should establish effective monitoring and alerting such that suspicious activities are detected and responded to quickly 
- Establish or adopt an incident response and recovery plan, such as National Institute of Standards and Technology (NIST) 800-61r2 or later

## 1.10 Server-Side request forgery (SSRF)
### 1.10.1 Scenario
If a network architecture is unsegmented (single broadcast domain), attackers can use connection results or elapsed time to connect or reject server-side request forgery (SSRF) payload connections to map out internal networks and determine if ports are open or closed on internal servers
### 1.10.2 Mitigation
- Sanitize and validate all client-supplied input data
- Enforce the URL schema, port, and destination with a positive allow list
- Do not send raw responses to clients
- Disable HTTP redirections
- Be aware of the URL consistency to avoid attacks such as DNS rebinding and “time of check, time of use” (TOCTOU) race conditions

# 2 NIST 800 63
## 2.1 Key Points on Password Management:
1. **Avoid Mandatory Periodic Password Changes**:
    - NIST advises against forcing users to change their passwords at regular intervals (e.g., every 60 or 90 days) without any evidence of compromise. This is based on the understanding that frequent password changes can lead to poor password practices, such as users choosing weaker passwords or making small predictable changes to their passwords.
2. **Focus on Password Strength and Complexity**:
    - Instead of periodic changes, the guidelines recommend enforcing strong passwords that are difficult to guess. Passwords should be at least 8 characters long and ideally longer. Users should be encouraged to use passphrases or a combination of upper and lower case letters, digits, and special characters.
3. **Use of Password Managers**:
    - NIST encourages the use of password managers to help users generate and store complex passwords securely.
4. **Screening Passwords Against Common Lists**:
    - Passwords should be screened against lists of commonly used, expected, or compromised passwords. This helps ensure that users do not select passwords that are easily guessable or have been exposed in data breaches.
5. **Implement Multi-Factor Authentication (MFA)**:
    - The guidelines emphasize the importance of multi-factor authentication (MFA) to enhance security. MFA provides an additional layer of security beyond just the password.
6. **Account Recovery and Secure Handling**:
    - NIST 800-63B also provides guidance on secure account recovery processes and the handling of forgotten passwords, ensuring that these processes do not become a weak link in security.

