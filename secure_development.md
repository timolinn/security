# Secure Software Development

On a high level I think this refers to being security minded when developing application software. There are different kinds of known vulnerabilities in software, top 5 are listed below. I should note that most according to studies, software vulnerabilities are higher on high-layer application software.

## Top 5 Application vulnerabilty

+ SQL Injection: Occurs when user input/query from things like HTML forms are not properly sanitized or escaped before sending to the database for execution. Easiest way to prevent against this is to use ORMs. [Read more](https://www.veracode.com/security/sql-injection)
+ Cross Site Scriptiong (XSS): Occurs when input data from web forms are not validated or sanitised and lacks proper html encoding on the output. Easiest way to prevent against this are: user input validation and sanitisation, escape and encode and user sourced data input before saving to the DB. [Read more](https://www.veracode.com/security/xss)
+ Insecure crypto: Use of poor encryption algorithms. Easiest way to prevent is by not writing your own crypto library.
+ Weak Access control and credentials management: This means application that do not implement "The principle least privilege (POLP)", password throttling. To prevent implement 2FA, password throttling and maintain POLP. [Read More](https://www.veracode.com/blog/intro-appsec/surviving-password-policy-perfect-storm)
+ Vulnerable Open Source Components: Open source code comes with certain risks, it's basically somone else's code you can't know what's really going on unless you perform full source code analysis. To prevent keep them updated and perform automatic software conposition analysis. [Read More here](https://www.veracode.com/security/open-source-component-risk)

To maintian a secure development pipeline, these 3 components must be considered. They are foundational this topic:

+ Technology
+ [Processess](https://www.veracode.com/sites/default/files/Resources/iPapers/find-your-appsec-zen/index.html)
+ Security Trainings

## Secure Development Lifecycle (SDL)

SDL introduces security and privacy practices in throughout development phases.

SDL consists of 5 phases:

+ **Requirements gathering** - Security requirements, setting up phase gates, risk management
+ **Architecture design** - Threat modeling, identity design
+ **Coding/Implementation** - Coding best practices, Static analysis
+ **Testing** - Vulnerability Assessment, Fuzzing
+ **Deployment** - Server configuration review, Network configuration review.

### Microsoft SDL principles

#### Security Principles (SD3+C)

+ **Secure by Design** -
+ **Secure by Default** -  POLP, conservative default settings.
+ **Secure in Deployment** - deployment guides, patch deployment tools.
+ **Communication** - Vulnerability response, community engagement.

#### Privacy Principles

+ **Privacy by Design** - Provide user with notice and consent before accessing sensitive data, protect storage and data transfer.
+ **Privacy by Default** - Ship with conservative default settings.
+ **Privacy in Deployment** - publish deployment guides.
+ **Communications** - Privacy response team, promote transparency.

### SDL-Agile

SDL has been adapted to work with agile development methodology (scrum). To achieve this SDL processes is divided into 3 different categries:

+ **Every Sprint tasks** - This comprise of tasks to perform during each sprint.
+ **Bucket tasks** - This comprises of tasks to perform occasionally during secure software development lifecycle.
+ **One-Time tasks** - This are tasks done just once in the entire lifecycle.

An ideal SDL-Agile lifecycle goes like this:

+ **Requirements Phase** - This is where the team establishes security requirements, qulaity gates, [bug bars](https://docs.microsoft.com/en-us/security/sdl/security-bug-bar-sample), security and privacy risks assessment. All these can be performed as _one time_ tasks.
+ **Design Phase** - here the team establishes design requirements (one time), __use threat modelling__ (bucket task), perform attack surface analysis and reduction (every sprint).
+ **Implementation Phase** - The team should ensure they use approved tools, perform static analysis and deprecate unsafe functions during every sprint.
+ **Verification Phase** - This is for testing for security nd privacy specifications by performing dynamic analysis (buffer overflows, etc), perform fuzz testing (feed the program with malformed data to see how the system handles this), conduct attack surface review. All these are can be dome as bucket tasks.
+ **Release Phase** - Here the team must create nad incident response plan (one time), conduct find security review (every sprint), certify release and archive (every sprint). The team must conduct FSR (Final Security Review) before release.
+ **Response Phase** - handles security issues and mobilises vulnerability response teams.

FSR:

+ All security and privacy issues must be fixed and completed.
+ Review threat models
+ validate results from security tools in use.

#### Reference

+ Microsoft SDL
+ IEC 62443-4-1
+ OWASP SAMM
+ BSIMM

## Secure Design Principles

+ Attack surface reduction - anywhere exposed and accessible to a human or malicious user eg. user interfaces.

  + Look at entry points: (network input/output), file inputs etc.
  + Rank entry points: Authenticated, admin or user-level access, TCP or UDP

### Do the following for lower attack surface

+ off by default
+ Closed socket
+ TCP instead of UDP (TCPs are more easily secured)
+ Authenticate users
+ Running as user instead of as SYSTEM
+ Local subnet accessible intead of online
+ User defined settings intead of Uniform defaults
+ Small code
+ Strong access control

+ Basic privacy - Empower users to manage their personal information.
+ Threat modelling - A process to understand possible threats to an application
+ Defense in depth - if one defense layer fails, what other layers of defense can protect the app? eg, firewall, ip security etc.
+ Least privilege - What is the minimum access level the application to perform it's functions? Elevate privileges only when needed, and then release after the operation is complete. Incase of a breach in security, the level of damage is minimized.
+ Secure default - Set default settings of your application to the most secure  values. Keep it upto the user to reduce security and privacy levels. eg, turn on client side complex passwords by default.
