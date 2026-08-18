1. Module Overview
Module 6 mainly focuses on:
•	Web application security 
•	Insecure coding practices 
•	Authentication and session weaknesses 
•	Input validation 
•	Techniques attackers use to exploit web applications 
Main Idea
A secure application is not only about finding vulnerabilities after development.
Security should be built into the application from the beginning.
This is called:
Shift-Left Security
________________________________________
2. Shift-Left Security
Shift-left security means introducing security practices early in the software development lifecycle, rather than waiting until the application is finished.
Example
Developer writes code
        ↓
Code is committed
        ↓
Automated security scanner checks it
        ↓
Developer fixes vulnerabilities
Why It Matters
When developers receive security feedback during development:
•	Vulnerabilities can be fixed earlier. 
•	Fixing bugs is generally easier. 
•	Developers learn from their mistakes. 
•	The same insecure coding practices are less likely to be repeated. 
________________________________________
3. Insecure Coding Practices
Insecure coding can introduce vulnerabilities that attackers may exploit.
Important examples include:
•	Sensitive information in source-code comments 
•	Poor error handling 
•	Hard-coded credentials 
•	Race conditions 
•	Unprotected APIs 
•	Hidden form fields 
•	Lack of code signing 
________________________________________
4. Sensitive Information in Comments
Developers sometimes leave sensitive information inside source-code comments.
Examples
// Database password: admin123
// API key: ABC123...
// Temporary admin account: testadmin
An attacker who obtains the source code may discover these secrets.
Security Issue
CWE-615 — Information Exposure Through Comments
Comments Should Never Contain
•	Passwords 
•	API keys 
•	Authentication tokens 
•	Private keys 
•	Internal secrets 
________________________________________
5. Improper / Verbose Error Handling
Applications sometimes display too much information when an error occurs.
Dangerous Error Information Can Include
•	Error codes 
•	Database errors 
•	SQL statements 
•	Stack traces 
•	File paths 
•	Software versions 
•	Internal configuration details 
This information can help attackers understand the application's internal structure and identify additional attack opportunities.
Example
Instead of:
SQL Error: MySQL syntax error near users.php line 42
A safer application might display:
An unexpected error occurred. Please try again later.
Detailed diagnostic information should be available to developers/support staff, but should not be exposed to attackers.
________________________________________
6. Hard-Coded Credentials
Hard-coded credentials are usernames, passwords, API keys, or other secrets directly embedded in application code.
Example
username = "admin"
password = "Password123"
This is extremely dangerous because anyone who obtains the source code may obtain the credentials.
CWE
CWE-798 — Use of Hard-coded Credentials
Possible Impact
Hard-coded credentials may allow an attacker to:
•	Access the application 
•	Access databases 
•	Access servers 
•	Access APIs 
•	Completely compromise systems 
Better Approach
Use secure:
•	Secret management systems 
•	Environment variables 
•	Credential vaults 
•	Key-management systems 
________________________________________
7. Race Conditions
A race condition occurs when two or more operations happen close together or simultaneously, but the application requires them to happen in a specific order.
An attacker may exploit a small timing window between a security check and the actual operation.
TOCTOU
Race conditions are commonly associated with:
Time-of-Check to Time-of-Use (TOCTOU)
Simple Example
Imagine an application:
1.	Checks whether an account has enough money. 
2.	Performs the withdrawal. 
If an attacker can trigger multiple withdrawals between these operations, the application might incorrectly allow more money to be withdrawn than should be possible.
Important Point
Race-condition attacks are generally difficult to exploit because precise timing is often required.
________________________________________
8. APIs
API = Application Programming Interface
APIs allow applications and systems to communicate with each other.
Modern applications heavily rely on APIs.
Examples
•	Mobile applications communicating with servers 
•	Websites communicating with backend services 
•	Online dashboards 
•	Payment systems 
•	Cloud services 
________________________________________
9. Major API Technologies
Three important API technologies discussed in this module are:
SOAP
SOAP = Simple Object Access Protocol
Characteristics:
•	Standards-based web-services protocol 
•	Originally developed by Microsoft 
•	Uses XML 
•	Has a more strict messaging structure 
•	Commonly found in older/legacy applications 
________________________________________
REST
REST = Representational State Transfer
Characteristics:
•	Generally easier to use than SOAP 
•	Commonly uses JSON 
•	Uses HTTP 
•	Commonly documented with: 
o	Swagger 
o	OpenAPI Specification 
REST APIs are extremely common in modern web applications.
________________________________________
GraphQL
GraphQL is a query language for APIs.
It provides developer tools and is commonly used by:
•	Mobile applications 
•	Web applications 
•	Online dashboards 
________________________________________
10. SOAP vs REST vs GraphQL
Technology	Main Characteristic
SOAP	XML-based web-services protocol
REST	API style commonly using JSON and HTTP
GraphQL	Query language for APIs
Easy Memory
SOAP → XML
REST → JSON + HTTP
GraphQL → Query Language
________________________________________
11. HTTPS and TLS
APIs should use HTTPS rather than plain HTTP.
HTTPS
HTTPS is the secure version of HTTP.
It uses TLS (Transport Layer Security) to encrypt communication.
This helps protect sensitive information while it travels between the client and server.
________________________________________
12. API Documentation
API documentation can reveal how an application works.
For a penetration tester, API documentation can provide valuable information about:
•	Endpoints 
•	Parameters 
•	Requests 
•	Data structures 
•	Authentication 
•	Available functionality

12. API Documentation Formats
Important API documentation formats include:
Swagger / OpenAPI
Used for documenting, designing, and developing APIs.
WSDL
WSDL = Web Services Description Language
•	XML-based 
•	Used to describe web services 
WADL
WADL = Web Application Description Language
•	XML-based 
•	Used to describe web applications 
________________________________________
13. API Testing During Penetration Testing
When testing an API, capture the complete HTTP request, not just the URL.
Tools such as:
•	Burp Suite 
•	OWASP ZAP 
can work as web proxies and capture HTTP requests.
Look for:
•	Unusual parameters 
•	Abnormal HTTP headers 
•	IDs in URLs 
•	Numbers that change between requests 
•	Dates 
•	JSON parameters 
•	XML parameters 
•	Other structured values 
These can provide clues about how the API processes data.
________________________________________
14. API Parameter Enumeration
Suppose you observe URLs such as:
/s/abcd/page
/s/dead/page
/s/beef/page
The changing values:
abcd
dead
beef
may represent an API parameter rather than an actual directory.
Identifying changing parameters can help penetration testers understand how an application handles requests and resources.
________________________________________
15. API Fuzzing
Fuzzing is an automated testing technique that sends unexpected, malformed, or unusual input to an application.
Goals of fuzzing
Fuzzing can help identify:
•	Application crashes 
•	Input-validation problems 
•	Unexpected behavior 
•	Security vulnerabilities 
Example Inputs
A tester may send:
•	Very large values 
•	Special characters 
•	Unicode characters 
•	Invalid data types 
•	Unexpected parameters 
The tester then observes how the application responds.
________________________________________
16. Radamsa
Radamsa is a fuzzing tool that generates modified or malformed test data.
It can be used to test:
•	Applications 
•	Protocols 
•	Parameters 
Its purpose is to generate unusual input that can reveal unexpected application behavior.
________________________________________
17. API Security Best Practices
Important API security recommendations include:
1. Use HTTPS
Use HTTPS with strong and properly configured TLS.
2. Validate Parameters
Applications should verify that incoming parameters contain valid and expected data.
3. Sanitize Input
Input should be handled safely before being processed or used.
4. Detect Attack Patterns
Applications should monitor for common attack patterns and malicious input.
5. Use Strong Authentication
Use appropriate authentication mechanisms to verify users and systems.
6. Use Strong Authorization
Users should only be able to access resources they are authorized to access.
7. Use Reputable Libraries
Use trusted and well-maintained libraries instead of unnecessarily creating security-sensitive functionality from scratch.
8. Separate API Security from Application Logic
Security controls can be implemented in a separate security layer or tier where appropriate.
9. Identify Sensitive Data
Organizations should know which information is:
•	Public 
•	Internal 
•	Sensitive 
•	Confidential 
Sensitive information should receive appropriate protection.
10. Perform Security Reviews
Whenever possible, security professionals should review API implementations and security controls.
________________________________________
18. Hidden Elements
Web applications may contain hidden HTML form fields.
Example
<input type="hidden" name="price" value="100.00">
Although the field is not normally visible to the user, its value is still sent to the server.
An attacker may modify the value.
Example
Original:
price=100
Modified:
price=1
If the server blindly trusts this value, the application may be vulnerable to parameter tampering.
Important
Hidden does NOT mean secure.
The server must independently validate important values rather than trusting values supplied by the client.
Hidden fields can have legitimate purposes, including certain CSRF-related mechanisms, so a hidden field is not automatically a vulnerability.
________________________________________
19. Code Signing
Code signing uses a digital signature to verify that software:
1.	Comes from the expected developer or source. 
2.	Has not been modified after signing. 
It involves:
•	Private keys 
•	Public keys 
•	Digital signatures 
•	Trusted certificate authorities, where applicable 
Basic Process
Developer:
Software → Sign with Private Key

System/User:
Software → Verify Signature with Public Key
If the software is modified after it was signed, signature verification may fail.
________________________________________
20. Subresource Integrity (SRI)
SRI = Subresource Integrity
SRI allows a web page to specify a cryptographic hash for an external resource.
The browser can then verify that the downloaded resource matches the expected hash.
Purpose
SRI helps protect against modification or tampering of external resources such as:
•	JavaScript files 
•	Other externally loaded resources 
Basic Idea
Expected Hash
      ↓
Downloaded Resource
      ↓
Hash Comparison
      ↓
Match → Resource accepted
Mismatch → Resource rejected
________________________________________
21. Web Proxies
A web proxy can sit between a browser and a web application:
Browser ↔ Proxy ↔ Web Application
A penetration tester can use a proxy to:
•	Intercept requests 
•	Inspect requests 
•	Modify requests 
•	Forward requests 
•	Analyze responses 
Web proxies are extremely useful during web application penetration testing.
________________________________________
22. Burp Suite
Burp Suite is a popular web application security testing platform.
It includes a web proxy that can intercept HTTP/HTTPS traffic.
Editions
•	Community Edition 
•	Professional Edition 
Common Uses
Burp Suite can be used for:
•	Intercepting requests 
•	Modifying parameters 
•	Examining cookies 
•	Testing authentication 
•	Testing authorization 
•	Analyzing application behavior 
________________________________________
23. OWASP ZAP
OWASP ZAP = Zed Attack Proxy
OWASP ZAP is a free and open-source web application security testing tool.
It provides features such as:
•	Web proxy 
•	Automated scanning 
•	Fuzzing 
•	Vulnerability detection 
ZAP can help security testers identify and investigate vulnerabilities in web applications.
________________________________________
24. Burp Suite vs OWASP ZAP
Feature	Burp Suite	OWASP ZAP
Web proxy	✅	✅
Intercept traffic	✅	✅
Modify requests	✅	✅
Automated scanning	✅	✅
Fuzzing	✅	✅
Free version	Community Edition	Free/Open Source
Module Practice Question
Which tools can be used to intercept and forward web traffic?
•	Burp Suite 
•	OWASP ZAP 
________________________________________
25. Directory and File Enumeration Tools
These tools help discover files and directories on web servers.
Gobuster
•	Written in Go 
•	Used for directory and file enumeration 
•	Uses wordlists 
FFUF
•	Written in Go 
•	A fast web fuzzer 
•	Can be used for web enumeration and fuzzing 
Feroxbuster
•	Written in Rust 
•	Used for web reconnaissance and fuzzing 
DirBuster
Used to discover directories and files on web servers.
________________________________________
26. Wordlists
Enumeration tools commonly use wordlists.
A wordlist is a file containing many possible values that a tool can test.
Example
admin
login
dashboard
backup
uploads
api
config
The tool can use these values to test whether corresponding resources exist on the target.
________________________________________
27. OWASP WSTG
OWASP WSTG = OWASP Web Security Testing Guide
It is an important resource for web application security testing.
It provides guidance on:
•	Web application security testing 
•	Vulnerability identification 
•	Testing methodologies 
•	Security recommendations 
•	Vulnerability mitigation 
For penetration testers, the WSTG is an important reference when conducting web application security assessments.
________________________________________
28. ZAP + WSTG
The module demonstrates combining:
OWASP WSTG → Methodology and Reference
with:
OWASP ZAP → Practical Scanning and Testing
Together, they can help testers:
1.	Identify potential vulnerabilities. 
2.	Investigate findings. 
3.	Understand the vulnerability. 
4.	Determine the underlying cause. 
5.	Identify appropriate mitigation guidance. 
________________________________________
29. Important Vulnerability Concepts
The following concepts from Module 6 are important to understand.
Information Exposure
Sensitive information is accidentally exposed to unauthorized users.
Improper Error Handling
Application errors reveal information that could help attackers.
Hard-Coded Credentials
Credentials are directly embedded into application source code.
Race Condition
An attacker exploits timing or an incorrect sequence between operations.
API Security Issues
APIs lack adequate:
•	Authentication 
•	Authorization 
•	Input validation 
•	Other necessary security controls 
Parameter Tampering
An attacker modifies application parameters to change application behavior.
Lack of Code Signing
The authenticity and integrity of software cannot be reliably verified.
________________________________________
30. Important CWE Numbers
CWE	Vulnerability
CWE-615	Information Exposure Through Comments
CWE-798	Use of Hard-coded Credentials
CWE-227	API Abuse
________________________________________
31. Tools to Remember
Tool	Main Purpose
Burp Suite	Web proxy and security testing
OWASP ZAP	Proxy, scanning, and fuzzing
Gobuster	Directory/file enumeration
FFUF	Fast web fuzzing
Feroxbuster	Web reconnaissance/fuzzing
DirBuster	Directory enumeration
Radamsa	Fuzzing/test-data generation
________________________________________
32. High-Value Concepts
Shift Left
Security testing should begin early in the software development lifecycle.
Hidden ≠ Secure
A hidden HTML field can still be modified by the client.
Error Messages
Detailed error messages can reveal useful information to attackers.
Hard-Coded Credentials
Passwords, API keys, and other secrets should not be directly embedded in source code.
Race Condition
Think:
Timing + Incorrect Sequence + Small Exploitation Window
API Testing
Do not inspect only URLs. Capture and analyze the complete HTTP requests.
Fuzzing
Think:
Automated unusual/malformed input → Observe application behavior
Code Signing
Think:
Digital Signature → Authenticity + Integrity
SRI
Think:
Cryptographic Hash → Verify External Resource Integrity
Web Proxy
Think:
Browser → Proxy → Server
A proxy allows security testers to intercept, inspect, and modify HTTP/HTTPS traffic.
 
