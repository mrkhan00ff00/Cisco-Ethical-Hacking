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
________________________________________
Module 7 — Cloud & Specialized Systems Security
1. Module Overview
Module 7 focuses on security risks associated with cloud technologies and specialized systems.
It covers:
•	Cloud computing models 
•	Cloud attack vectors 
•	Credential harvesting 
•	Privilege escalation 
•	Account takeover 
•	Metadata service attacks 
•	Misconfigured cloud assets 
•	Denial-of-Service and resource exhaustion 
•	Malware injection 
•	Side-channel attacks 
•	Mobile security 
•	IoT security 
•	IoT protocols 
•	Management interfaces 
•	Virtual machine vulnerabilities 
•	Container and Kubernetes security 
Main Idea
Modern infrastructure is no longer limited to traditional servers.
Organizations now use:
•	Cloud services 
•	Mobile devices 
•	IoT devices 
•	Virtual machines 
•	Containers 
•	Kubernetes 
Each technology introduces its own security risks.
________________________________________
Part 1 — Cloud Computing
2. What Is Cloud Computing?
Cloud computing provides computing resources and services over a network instead of requiring organizations to maintain everything locally.
Cloud resources can include:
•	Computing power 
•	Storage 
•	Applications 
•	Databases 
•	Networking 
•	Development platforms 
Cloud environments are powerful and flexible, but they can be difficult to secure because resources can be created quickly and may sometimes be forgotten or incorrectly configured.
________________________________________
3. Why Cloud Security Is Important
Cloud environments may contain:
•	Sensitive information 
•	Application code 
•	User accounts 
•	Databases 
•	Credentials 
•	Intellectual property 
A compromised cloud environment can potentially result in:
•	Data theft 
•	Data exfiltration 
•	Data deletion 
•	Privacy violations 
•	Account compromise 
•	Service disruption 
Cloud security shares many principles with traditional IT security, but cloud environments introduce additional complexity.
________________________________________
4. CapEx vs OpEx
Organizations may move to cloud computing partly because it changes how infrastructure costs are managed.
CapEx — Capital Expenditure
Money spent on long-term physical infrastructure.
Examples
•	Purchasing servers 
•	Purchasing networking equipment 
•	Building data centers 
OpEx — Operating Expenditure
Ongoing operational costs.
Examples
•	Paying for cloud computing resources 
•	Paying for storage 
•	Paying for cloud services 
Cloud computing commonly allows organizations to move from CapEx toward OpEx.
________________________________________
5. Advantages of Cloud Computing
Important advantages include:
•	Distributed storage 
•	Scalability 
•	Resource pooling 
•	Access from almost anywhere 
•	Measured services 
•	Automated management 
________________________________________
6. Essential Characteristics of Cloud Computing
According to the material, important characteristics include:
1. On-Demand Self-Service
Users can provision resources when they need them.
2. Broad Network Access
Services can be accessed through networks using different types of devices.
3. Resource Pooling
Cloud resources are shared among multiple customers or users.
4. Rapid Elasticity
Resources can quickly scale up or down according to demand.
5. Measured Service
Cloud resource usage can be monitored and measured.
________________________________________
7. Cloud Deployment Models
Public Cloud
Cloud infrastructure is available for public use.
Private Cloud
Cloud infrastructure is dedicated to a particular organization.
It may exist:
•	On-premises 
•	In a dedicated provider environment 
Community Cloud
Cloud infrastructure is shared by multiple organizations with common requirements.
Hybrid Cloud
A hybrid cloud combines two or more cloud environments.
For example:
Private Cloud + Public Cloud
It may also combine cloud infrastructure with on-premises infrastructure.
________________________________________
8. Cloud Service Models
There are three major cloud service models.
IaaS — Infrastructure as a Service
Provides infrastructure resources such as:
•	Virtual machines 
•	Storage 
•	Networking 
The customer has significant control over the infrastructure.
________________________________________
PaaS — Platform as a Service
Provides a platform for developing and running applications.
The cloud provider manages much of the underlying infrastructure.
________________________________________
SaaS — Software as a Service
Provides a complete application to users.
Users generally access the software through the internet rather than managing the underlying infrastructure.
Easy Memory
IaaS → Infrastructure
PaaS → Platform
SaaS → Software
________________________________________
Part 2 — Cloud Attack Types
9. Credential Harvesting
Credential harvesting means stealing authentication information.
This can include:
•	Usernames 
•	Passwords 
•	Tokens 
•	PINs 
•	Session credentials 
A common method is phishing.
Typical Flow
Attacker
   ↓
Fake Login Page
   ↓
Victim Enters Credentials
   ↓
Attacker Receives Credentials
Attackers may create fake versions of legitimate cloud login pages.
________________________________________
10. MFA and Credential Harvesting
MFA = Multi-Factor Authentication
MFA provides additional authentication factors beyond a password.
It significantly improves protection against ordinary password theft.
However, some attacks may attempt to steal session information, so MFA alone is not a complete defense against every possible attack.
Important Idea
Password + MFA ≠ Absolute Security
Organizations should also consider:
•	Phishing-resistant authentication 
•	Session protection 
•	Monitoring 
•	User awareness 
________________________________________
11. SSO and Federated Authentication
SSO — Single Sign-On
SSO allows users to access multiple services using a common authentication mechanism.
Federated Authentication
Federated authentication allows authentication between different organizations or services using trusted identity relationships.
These technologies improve usability, but they can become attractive targets because compromising an identity provider may provide access to multiple connected services.
________________________________________
12. Privilege Escalation
Privilege escalation occurs when an attacker gains more privileges than they are authorized to have.
Example
Normal User → Administrator
________________________________________
Vertical Privilege Escalation
The attacker moves upward to a higher privilege level.
Example:
Normal User → Administrator
Horizontal Privilege Escalation
The attacker accesses another user's resources while remaining at approximately the same privilege level.
Example:
User A → User B's Data
Easy Difference
Vertical = Higher privileges
Horizontal = Another user's resources
________________________________________
13. Account Takeover
An account takeover occurs when an attacker gains control of a legitimate user or application account.
After compromising one account, the attacker may attempt to access:
•	Other accounts 
•	Cloud resources 
•	Applications 
•	Databases 
•	Sensitive information 
This makes strong authentication, authorization, monitoring, and account protection important parts of cloud security.

13. Account Takeover
An account takeover occurs when an attacker gains control of a legitimate user or application account.
After compromising an account, an attacker may attempt to access:
•	Sensitive information 
•	Cloud resources 
•	Applications 
Indicators of Account Takeover
Organizations can monitor for:
•	Unusual login locations 
•	Repeated failed login attempts 
•	Lateral phishing emails 
•	Suspicious OAuth, SAML, or OpenID Connect connections 
•	Abnormal file sharing 
•	Unusual downloads 
________________________________________
14. Metadata Service Attacks
Cloud platforms may provide metadata services that applications use to obtain temporary credentials and configuration information.
These services can contain highly valuable information.
For example, a cloud virtual machine may request temporary credentials through its metadata service.
Why Attackers Target Metadata Services
If an attacker can improperly access a metadata service, they may obtain:
•	Access keys 
•	Secret credentials 
•	Temporary tokens 
•	Instance information 
•	Configuration information 
Important Security Concept
Cloud applications should prevent untrusted users or applications from accessing sensitive metadata-service endpoints.
________________________________________
15. Misconfigured Cloud Assets
Cloud misconfiguration is a major security problem.
IAM
IAM = Identity and Access Management
Incorrect permissions can allow users to access resources they should not be able to access.
Federation
Incorrectly configured identity relationships can create unauthorized access.
Object Storage
Cloud storage can accidentally become publicly accessible.
Containers
Incorrectly configured container environments can expose applications and data.
Key Lesson
A secure cloud service can still become insecure because of incorrect configuration.
________________________________________
16. Resource Exhaustion and DoS
DoS
DoS = Denial of Service
A DoS attack attempts to make a service unavailable to legitimate users.
DDoS
DDoS = Distributed Denial of Service
A DDoS attack uses multiple systems to generate attack traffic against a target.
Important Measurements
bps — Bits per Second
Usually associated with overwhelming network bandwidth or links.
pps — Packets per Second
Often targets network equipment and infrastructure.
rps — Requests per Second
Often targets application or web servers.
________________________________________
17. Direct-to-Origin Attack
A Direct-to-Origin (D2O) attack attempts to discover the original server's IP address behind a CDN or proxy.
Normally:
User → CDN/Proxy → Origin Server
If the attacker discovers the origin server:
Attacker → Origin Server
The attacker may be able to bypass protections provided by the CDN or proxy.
________________________________________
18. CDN
CDN = Content Delivery Network
A CDN uses geographically distributed servers or proxies to help provide:
•	Better performance 
•	High availability 
•	Distributed content delivery 
________________________________________
19. Cloud Malware Injection
In a cloud malware injection attack, an attacker attempts to introduce a malicious application or instance into a cloud environment.
If successful, the malicious instance may provide a foothold for further attacks.
Possible Consequences
•	Backdoors 
•	Data theft 
•	Eavesdropping 
•	Data manipulation 
•	Covert communication 
________________________________________
20. Side-Channel Attacks
A side-channel attack obtains information from indirect characteristics of a system rather than directly exploiting its intended functionality.
Possible information sources include:
•	Timing 
•	Power consumption 
•	Electromagnetic emissions 
•	Sound 
•	Hardware behavior 
Attackers may attempt to extract:
•	Credentials 
•	Cryptographic keys 
•	Sensitive information 
Spectre and Meltdown
Spectre and Meltdown are examples of processor vulnerabilities associated with side-channel attacks.
They affected various processor architectures and could potentially expose sensitive information.
________________________________________
Part 3 — Mobile Security
21. Mobile Device Attacks
Mobile applications and devices have unique security risks.
One important technique is reverse engineering.
Reverse engineering involves analyzing a compiled mobile application to understand:
•	Application structure 
•	Application logic 
•	APIs 
•	Embedded information 
•	Potential weaknesses 
Attackers may use reverse engineering to discover vulnerabilities or compromise mobile platforms.
________________________________________
22. Common Mobile Vulnerabilities
Insecure Storage
Sensitive information may be stored insecurely on a device.
Examples:
•	Passwords 
•	Tokens 
•	Personal data 
Passcode and Biometric Vulnerabilities
Weak authentication mechanisms or incorrect biometric implementations can allow unauthorized access.
Certificate Pinning Problems
Certificate pinning helps an application verify that it is communicating with the expected certificate or endpoint.
Incorrect implementation can weaken application security.
Vulnerable Components
Applications may contain outdated or vulnerable third-party libraries or components.
Excessive Permissions
Applications should not receive more permissions than necessary.
This relates to the:
Principle of Least Privilege
Give an application only the permissions it actually needs.
For example, a game should not unnecessarily have access to sensitive device resources.
Business Logic Vulnerabilities
An application may technically function as designed, but the design itself may allow unintended or insecure behavior.
________________________________________
23. Mobile Security Tools
Tool	Purpose
Burp Suite	Web/API traffic interception and testing
Drozer	Android security testing and exploitation framework
Needle	Mobile application security testing
MobSF	Automated mobile application and malware analysis
Postman	API development and testing
Ettercap	On-path/network attacks
Frida	Dynamic instrumentation
Objection	Mobile runtime security testing
Android SDK Tools	Android development and testing
ApkX	Decompiles Android APK files
APK Studio	Android APK analysis and reverse engineering
________________________________________
24. Important Tool Matches
Remember these:
•	ApkX → Decompiles APK files 
•	Postman → API testing and development 
•	Drozer → Android security testing 
•	Frida → Dynamic instrumentation 
•	Ettercap → On-path attacks 
•	MobSF → Automated mobile application/malware analysis 
________________________________________
Part 4 — IoT Security
25. What Is IoT?
IoT = Internet of Things
IoT includes internet-connected physical devices such as:
•	Sensors 
•	Cameras 
•	Smart devices 
•	Industrial equipment 
•	Gateways 
•	Monitoring systems 
IoT environments can include:
•	SCADA 
•	IIoT 
•	ICS 
•	Smart home systems 
•	Transportation systems 
________________________________________
26. Why IoT Security Is Difficult
IoT environments are complicated because they often involve:
•	Different hardware 
•	Different software 
•	Legacy technologies 
•	Multiple vendors 
•	Multiple integrators 
•	Different device limitations 
•	Cloud services 
•	Network gateways 
There is no single security solution that works for every IoT environment.
Three Important Reasons
1.	Legacy technologies 
2.	Multiple vendors and integrators 
3.	Disparate hardware and software 
________________________________________
27. IoT Architecture
A simplified IoT architecture can be represented as:
Endpoints → Gateways/Fog → Cloud → Applications
Endpoints
The actual IoT devices or "things."
Gateways/Fog Layer
Intermediate devices such as:
•	Routers 
•	Switches 
•	Computing platforms 
Cloud
Provides:
•	Storage 
•	Processing 
•	Other cloud services 
Applications
Use collected information to provide business functionality.
________________________________________
28. Common IoT Protocols
Important IoT protocols include:
•	Wi-Fi 
•	Bluetooth 
•	Bluetooth Low Energy (BLE) 
•	Zigbee 
•	Z-Wave 
•	LoRaWAN 
•	Insteon 
•	Modbus 
•	Siemens S7comm 
________________________________________
29. Bluetooth Low Energy (BLE)
BLE is widely used in:
•	Home devices 
•	Medical equipment 
•	Industrial devices 
•	Government equipment 
BLE Connection Establishment
Phase 1: Pairing and feature exchange
Phase 2: Short-term key generation
Phase 3: Transport-specific key distribution
BLE supports cryptographic functions including AES.
However, some devices may fail to implement encryption properly.
________________________________________
30. BLE Security Problems
Attackers may:
•	Scan BLE devices 
•	Listen to advertisements 
•	Identify poorly configured devices 
•	Create fake or cloned BLE devices 
•	Perform on-path attacks 
Important Tools
Ubertooth One
Specialized hardware for Bluetooth/BLE research.
GATTacker
Can be used to test BLE implementations and perform on-path attacks.
BtleJuice
A framework for intercepting and manipulating BLE traffic.
________________________________________
31. IoT Security Considerations
IoT devices often have limited computing resources.
This creates a security challenge because some devices may not have sufficient resources to support strong security mechanisms.
For example, encryption may not be properly supported.
This is sometimes described as a fragile environment concern.
Other concerns include:
•	Availability 
•	Data corruption 
•	Data exfiltration 
________________________________________
32. Common IoT Vulnerabilities
Insecure Defaults
Devices may ship with default:
•	Usernames 
•	Passwords 
•	Configurations 
These should be changed.
Plaintext Communication
Data may be transmitted without encryption, potentially exposing sensitive information.
Hard-Coded Configurations
Important configuration information may be permanently embedded into devices or software.
Outdated Firmware
Old firmware may contain known vulnerabilities.
Devices should support security updates.
________________________________________
33. IoT Security Checklist
For networked IoT devices, verify that:
•	Default credentials have been changed. 
•	Default configurations have been changed. 
•	Firmware/software can be updated. 
•	Communications support encryption. 
________________________________________
Part 5 — IoT Management Interfaces
34. IPMI
IPMI = Intelligent Platform Management Interface
IPMI provides remote management and monitoring capabilities.
It can allow administrators to manage systems even when the operating system is:
•	Offline 
•	Unresponsive 
•	Powered off 
________________________________________
35. BMC
BMC = Baseboard Management Controller
The BMC controls and monitors hardware.
Because it has significant access to the underlying hardware, compromising a BMC can be extremely serious.
An attacker who compromises a BMC could potentially:
•	Monitor the system 
•	Reboot it 
•	Modify system behavior 
•	Install malicious software or implants 
Key Idea
BMC access can be similar to physical access to the underlying system.
________________________________________
Part 6 — Virtual Machines
36. Virtual Machines
A virtual machine (VM) is intended to provide an isolated computing environment.
Multiple VMs can run on the same physical machine.
A hypervisor manages these virtual machines.
________________________________________
37. Type 1 Hypervisor
Also called a:
Bare-metal / Native Hypervisor
It runs directly on physical hardware.
Examples
•	VMware ESXi 
•	Proxmox 
•	Xen 
•	Microsoft Hyper-V 
________________________________________
38. Type 2 Hypervisor
Also called a:
Hosted Hypervisor
It runs on top of an existing operating system.
Examples
•	VirtualBox 
•	VMware Workstation 
•	VMware Player 
Easy Memory Trick
Type 1 → Hardware → Hypervisor → VM

Type 2 → Operating System → Hypervisor → VM
________________________________________
39. VM Escape
A VM escape vulnerability allows an attacker to break out of a virtual machine's isolation.
Potential impact:
Compromised VM → Hypervisor/Host → Other VMs
This is particularly serious because the attacker may potentially access other virtual environments.
________________________________________
40. Hyperjacking
Hyperjacking involves compromising or controlling the hypervisor.
An attacker may attempt to introduce a malicious hypervisor or gain control of the existing hypervisor.
Because the hypervisor manages the virtual environment, compromising it can have widespread consequences.
Remember
VM Escape → Escape from the VM
Hyperjacking → Attack or control the hypervisor
________________________________________
41. VM Repository Vulnerabilities
Organizations often download ready-made VM images from repositories or marketplaces.
Attackers may upload:
•	Fake VMs 
•	Impersonated VMs 
•	Backdoored VMs 
•	Malicious software 
If an organization deploys a malicious VM image, the attacker may gain a foothold in the environment.
Security Lesson
Do not blindly trust downloaded VM images.
Use trusted sources and verify images whenever possible.
________________________________________
Part 7 — Container Security
42. Evolution of Computing
The module describes an evolution:
Physical Servers
       ↓
Virtual Machines
       ↓
Containers/Kubernetes
       ↓
Serverless
As flexibility increases, the attack surface can also change.
________________________________________
43. Containers
Containers package applications and their dependencies into isolated environments.
Examples include:
•	Docker 
•	containerd 
•	Rocket 
Container environments can introduce vulnerabilities in:
•	Container images 
•	Software inside containers 
•	Host operating system 
•	Container/host interaction 
•	Runtime environment 
•	Kubernetes/orchestration 
________________________________________
44. Container Security Layers
When securing containers, consider:
1. Container Image
Check images for vulnerabilities and malicious content.
2. Software Inside the Container
Keep packages and applications updated.
3. Host Operating System
The host must also be properly secured.
4. Container ↔ Host Interaction
Prevent containers from obtaining unnecessary access to the host.
5. Runtime/Kubernetes
Secure the runtime environment and orchestration platform.
________________________________________
45. Container Security Development Process
A secure container lifecycle can be viewed as:
Develop → Deliver → Deploy
Develop
Use:
•	Secure coding 
•	Shift-left security 
•	Security scanning 
Deliver
Use:
•	Secure repositories 
•	Secure user access 
•	Image verification 
Deploy
Use:
•	Runtime scanning 
•	CIS Benchmarks 
•	Security policies 
•	Proper access controls 
________________________________________
46. Containers Running as Root
Running containers with root privileges can be dangerous.
If an attacker exploits a vulnerability inside a container, excessive privileges can make the compromise more serious.
Principle
Avoid unnecessary root privileges.
This follows the Principle of Least Privilege.
________________________________________
47. CIS Benchmarks
CIS Benchmarks provide security configuration recommendations.
The module specifically mentions:
•	Docker 
•	Kubernetes 
They provide guidance for securely configuring these environments.
________________________________________
48. Container Security Tools
Grype
An open-source container vulnerability scanner.
Used to identify vulnerabilities in container images.
Clair
A container vulnerability analysis and scanning tool.
Dagda
An open-source static analysis tool for detecting:
•	Vulnerabilities 
•	Trojans 
•	Backdoors 
•	Malware 
in Docker images and containers.
kube-bench
Checks Kubernetes security configurations against the:
CIS Kubernetes Benchmark
kube-hunter
An open-source security tool designed to assess the security posture of Kubernetes clusters.
Falco
A threat-detection engine for Kubernetes and cloud-native environments.
________________________________________
49. Important Container Tool Matches
Remember:
•	Grype → Container vulnerability scanning 
•	Dagda → Docker/container static analysis 
•	kube-bench → CIS Kubernetes Benchmark 
•	kube-hunter → Kubernetes security assessment 
•	Falco → Threat detection 
________________________________________
50. Supply Chain Attacks
Attackers can insert malicious code into legitimate-looking container images.
For example, malicious images can be uploaded to public repositories.
Organizations may download and deploy them without realizing they have been compromised.
This is an example of a software supply-chain attack.
