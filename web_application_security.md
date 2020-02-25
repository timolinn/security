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

# XML external entities (XXE)
