# Web Application security best practices

## Top 10 Web application vulnerabilities:

+ Injection
+ Broken Authentication
+ Sensitive Data Exposure
+ XML External Entities (XXE)
+ Broken Access Control
+ Security Misconfiguration
+ Cross-Site Scripting (XSS)
+ Using Comnponents with Known Vulnerabilities
+ Insufficient Logging and monitoring

## Injection

This is the most common web application vulnerabiltiy. It includes:

+ SQL Injection
+ LDAP Injection
+ NoSQL Injection
+ ORM injection
+ OS commands injection

### Remediation

+ Parameterized queries
+ User input validation
+ Parameterized RDBMS stored procedures
+ Input sanitisation and HTML character encoding
+ Accepted character whitelisting
+ Use SQL LIMIT statement.
+ If the website supports ZIP file upload, do validation check before unzip the file. The check includes the target path, level of compress, estimated unzip size

## Broken Authentication

Authentication is the process of verifying that an individual, entity or website is who it claims to be. Authentication in the context of web applications is commonly performed by submitting a username or ID and one or more items of private information that only a given user should know.

### Known authentication attacks

+ Credential stuffing
+ default passwords
+ password spraying
+ Brute force attacks

### Broken Authentication Mitigation Methods

+ Multifactor auth
+ Login throttling (limit failed login)
+ Enforce password complexity
+ Perform password checking against "known" weak passwords.
+ Impement minimum (8 chars) and maximum (64 characters for Bcrypt hash algorittm) password length
+ Allow usage of all chaacters including unicode and whitespace
+ Require re-authentication for sensitive features
+ Use generic authentication error messages
+ Robust logging and monitoring, log and review all failures, lockouts etc in auth process.
+ Use OAuth in application to application communication

## Sensitive Data Exposure

As the name sounds, this is the exposure of sensitive user data stored in a database.

### Examples of sensitive data that require protecion

+ Passwords
+ Credit card numbers
+ Personal Credentials
+ Social Security Numbers
+ Health Information
+ Personally Identifiable Information (PII)
+ Other personal information that might be used to identify an individual

### Sensitive Data exposure Mitigation methods

+ Classify data processed, stored or transmitted by an application
+ Identify which data is sensitive according to privacy laws, regulatory requirements or business needs
+ Apply controls as per the classification
+ Use TLS connection with strong ciphers
+ Don't store sensitive data unnecessarily
+ Discard it as soon as possible or use PCI-DSS compliant tokenization or even trucation. Data that is not retained cannot be stolen
+ Make sure all sensitive data are encrypted when at rest.
+ Ensure upto date and strong standard algorithms, protocols and keys are in place; use proper key management.

## XML external entities (XXE)

An application is vulnerable to XXE attacks if it allows malicious XML uploads which can exploit vulnerable code and/or app dependencies. Most XML parsers are vulnerable by default.

### XXE Main attack vectors include:

+ The exploitation of vulnerable XML processors if malicious actors can upload XML.
+ Inclusion of hostile content in an XML document.
+ The exploitation of vulnerable code
+ The exploitation of vulnerable dependencies.
+ The exploitation of vulnerable integrations.

### XXE Mitigation methods

+ Whenever possinle use less complex data formats such as JSON and avoid serialization of sensitive data.
+ Patch or upgrade all XML processors and libraries in use by the application or on the underlying operating system.
+ Use dependency checkers
+ Disable XML external entity and DTD processing in all XML parsers inn the application, as per the OWASP Cheat Sheet XXE Prevention
+ Implement positive ("Whitelisting") server-side input validatio, filtering or sanitisation to prevent hostile data within XML documents, headers or nodes.
+ Verify thst XML or XSL file upload functinality validates incoming XML using XSD vaildation or similar

## Broken Acess Control

Access control means putting a limit to what and what a user has access to, in webdev-speak this can be pages or sections, specific information or data. Authorization is the process where requests to access a particular resource should be granted or denied.

### Common access control vulnerabilities include:

+ Bypassing access control by modifying the URL, internal application state, or the HTML page, or simply using a custom API attack tool
+ Allowing primary key to be changed to another user's record, permitting viewing or editing of someone else's account.
+ Elevation of privilege. AActing as a user being logged in, or acting as an admin when logged in as a user.
+ Metadata manipulation, such as replayin or tampering with the JWT access control token or a cookie or hidden field manipulated to elevate privilege or abusing JWT invalidation
+ CORS misconfiguration allows unathorized API access.
+ Force browsing to authenticated pages as an unauthenticated user or privileged pages as a standard user.

### Broken Access Control Mitigation techniques

+ Employ the principle of least privilege
+ Get rid of accounts you don't need.
+ Audit your servers and websites - who is doing what, and why.
+ If possible, apply multi-factor authentication to all access points.
+ Disable acces points until they are needed in order to reduce your access windows.
+ Remove unecessary services off your server.
+ Verify applications that are externerlly accessible versus applicationa that are tied to your network.
+ If you are deeloping a web application, bear in mind that a production box should not be the place to develop, test, or push updates without testing.
+ Access controls should also enforce record ownership not just read, update, create, delete any record.

## Security Misconfigurations
