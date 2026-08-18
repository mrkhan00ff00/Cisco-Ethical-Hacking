1. Module Overview

Module 6 mainly focuses on:

Web application security
Insecure coding practices
Authentication and session weaknesses
Input validation
API security
Web application testing
Techniques attackers use to exploit applications
Main Idea

Security should not be added only after an application is completed.

Security should be included from the beginning of the Software Development Lifecycle (SDLC).

This approach is called:

Shift-Left Security

2. Shift-Left Security

Shift-Left Security means introducing security practices early in the software development lifecycle instead of waiting until the application is finished.

Example
Developer writes code
        ↓
Code is committed
        ↓
Security scanner checks code
        ↓
Vulnerability is detected
        ↓
Developer fixes the issue
Why Is Shift-Left Important?
Vulnerabilities can be discovered earlier.
Bugs are generally easier to fix during development.
Developers learn secure coding practices.
Security problems are less likely to reach production.
Easy Memory

Shift Left → Security Early

3. Insecure Coding Practices

Insecure coding practices can introduce vulnerabilities that attackers may exploit.

Important Examples
Sensitive information in source-code comments
Improper error handling
Hard-coded credentials
Race conditions
Unprotected APIs
Hidden form fields
Lack of code signing
4. Sensitive Information in Comments

Developers sometimes accidentally leave sensitive information inside source-code comments.

Example
// Database password: admin123
// API key: ABC123
// Temporary admin account: testadmin

If an attacker obtains the source code, these secrets may be exposed.

CWE-615

CWE-615 — Information Exposure Through Comments

Comments Should Never Contain
Passwords
API keys
Authentication tokens
Private keys
Internal secrets
Easy Memory

Comments → No Secrets

5. Improper / Verbose Error Handling

Applications sometimes reveal too much information when an error occurs.

Dangerous Error Information

An error message might reveal:

Database errors
SQL statements
Stack traces
File paths
Software versions
Error codes
Internal configuration

This information can help attackers understand the application's internal structure.

Bad Example
SQL Error: MySQL syntax error near users.php line 42
Better Example
An unexpected error occurred.
Please try again later.

Detailed diagnostic information should be available to developers, but should not normally be exposed to users.

Easy Memory

Detailed Error → Information Leakage

6. Hard-Coded Credentials

Hard-coded credentials are usernames, passwords, API keys, or other secrets directly embedded inside application code.

Example
username = "admin"
password = "Password123"

This is dangerous because anyone who obtains the source code may obtain the credentials.

CWE-798

CWE-798 — Use of Hard-coded Credentials

Possible Impact

An attacker may gain access to:

Applications
Databases
Servers
APIs
Other systems
Better Approach

Use:

Secret management systems
Environment variables
Credential vaults
Key-management systems
Easy Memory

Hard-coded Password = Dangerous

7. Race Conditions

A race condition occurs when multiple operations happen close together or simultaneously, but the application expects them to occur in a specific order.

An attacker may exploit a small timing window between two operations.

TOCTOU

Race conditions are commonly associated with:

Time-of-Check to Time-of-Use

Simple Example

An application:

Checks whether an account has enough money.
Performs the withdrawal.

If multiple requests are processed at nearly the same time, an attacker may attempt to exploit the timing window and withdraw more than should be allowed.

Important Point

Race-condition attacks can be difficult because precise timing is often required.

Easy Memory

Race Condition → Timing + Wrong Sequence

8. APIs

API = Application Programming Interface

APIs allow different applications and systems to communicate with each other.

Examples
Mobile applications communicating with servers
Websites communicating with backend services
Online dashboards
Payment systems
Cloud services

Modern applications heavily depend on APIs, making API security extremely important.

9. Major API Technologies

There are three important API technologies discussed in this module:

SOAP

SOAP = Simple Object Access Protocol

Characteristics
Standards-based web-services protocol
Uses XML
Has a strict messaging structure
Commonly found in older or legacy applications
Easy Memory

SOAP → XML

REST

REST = Representational State Transfer

Characteristics
Commonly uses HTTP
Frequently uses JSON
Generally simpler than SOAP
Very common in modern applications
Often documented using Swagger/OpenAPI
Easy Memory

REST → JSON + HTTP

GraphQL

GraphQL is a query language for APIs.

It is commonly used by:

Mobile applications
Web applications
Online dashboards
Easy Memory

GraphQL → Query Language

10. SOAP vs REST vs GraphQL
Technology	Main Characteristic
SOAP	XML-based web-services protocol
REST	API style commonly using JSON and HTTP
GraphQL	Query language for APIs
Easy Memory

SOAP → XML

REST → JSON + HTTP

GraphQL → Query

11. HTTPS and TLS

APIs should use HTTPS rather than plain HTTP.

HTTPS

HTTPS is the secure version of HTTP.

It uses:

TLS — Transport Layer Security

TLS encrypts communication between the client and server.

Purpose

It helps protect sensitive information while it travels across the network.

Easy Memory

HTTPS → HTTP + TLS

12. API Documentation

API documentation can reveal how an application works.

For penetration testers, it may provide information about:

Endpoints
Parameters
Requests
Data structures
Authentication
Available functionality
Important Documentation Formats
Swagger / OpenAPI

Used for:

Designing APIs
Documenting APIs
Developing APIs
WSDL

WSDL = Web Services Description Language

XML-based
Used to describe web services
WADL

WADL = Web Application Description Language

XML-based
Used to describe web applications
13. API Testing During Penetration Testing

When testing an API, do not look only at the URL.

Capture and analyze the complete HTTP request.

Useful Tools
Burp Suite
OWASP ZAP

These tools can capture HTTP/HTTPS requests and responses.

Look For
Unusual parameters
HTTP headers
IDs in URLs
Numbers that change between requests
Dates
JSON parameters
XML parameters
Other structured values

These can provide clues about how the application processes data.

Easy Memory

API Testing → Analyze the Full Request

14. API Parameter Enumeration

Suppose you observe:

/s/abcd/page
/s/dead/page
/s/beef/page

The changing values:

abcd
dead
beef

may represent an API parameter rather than an actual directory.

Identifying changing parameters helps testers understand how the application handles requests and resources.

15. API Fuzzing

Fuzzing is an automated testing technique that sends unexpected, malformed, or unusual input to an application.

Goals of Fuzzing

Fuzzing can identify:

Application crashes
Input-validation problems
Unexpected behavior
Security vulnerabilities
Example Inputs

A tester may send:

Very large values
Special characters
Unicode characters
Invalid data types
Unexpected parameters

The tester then observes how the application responds.

Easy Memory

Fuzzing → Strange Input → Observe Response

16. Radamsa

Radamsa is a fuzzing tool that generates modified or malformed test data.

It can be used to test:

Applications
Protocols
Parameters
Purpose

Generate unusual input that may reveal unexpected application behavior.

Easy Memory

Radamsa → Fuzzing Data Generator

17. API Security Best Practices

Important API security practices include:

1. Use HTTPS

Use HTTPS with strong and properly configured TLS.

2. Validate Parameters

Verify that incoming parameters contain valid and expected data.

3. Sanitize Input

Handle input safely before processing it.

4. Detect Attack Patterns

Monitor for malicious input and common attack patterns.

5. Use Strong Authentication

Properly verify users and systems.

6. Use Strong Authorization

Users should only access resources they are authorized to access.

7. Use Reputable Libraries

Use trusted and maintained libraries.

8. Separate API Security From Application Logic

Security controls can be implemented in a separate security layer where appropriate.

9. Identify Sensitive Data

Classify information as:

Public
Internal
Sensitive
Confidential
10. Perform Security Reviews

Security professionals should review API implementations and controls whenever possible.

18. Hidden Elements

Web applications may contain hidden HTML form fields.

Example
<input type="hidden" name="price" value="100.00">

Although the field is not visible to the user, the value is still sent to the server.

An attacker may modify it.

Example

Original:

price=100

Modified:

price=1

If the server blindly trusts this value, the application may be vulnerable to parameter tampering.

Important

Hidden does NOT mean Secure.

The server must independently validate important values.

Hidden fields can have legitimate purposes, including some CSRF-related mechanisms, so a hidden field is not automatically a vulnerability.

Easy Memory

Hidden ≠ Secure

19. Code Signing

Code signing uses a digital signature to verify that software:

Comes from the expected developer/source.
Has not been modified after signing.
It Uses
Private keys
Public keys
Digital signatures
Trusted certificate authorities where applicable
Basic Process
Developer
   ↓
Software
   ↓
Sign with Private Key
   ↓
Signed Software
   ↓
Verify with Public Key

If the software is modified after signing, signature verification may fail.

Easy Memory

Code Signing → Authenticity + Integrity

20. Subresource Integrity (SRI)

SRI = Subresource Integrity

SRI allows a web page to specify a cryptographic hash for an external resource.

The browser compares the downloaded resource against the expected hash.

Basic Process
Expected Hash
      ↓
Downloaded Resource
      ↓
Hash Comparison
      ↓
Match → Accepted
Mismatch → Rejected
Protects Resources Such As
JavaScript files
Other externally loaded resources
Easy Memory

SRI → Hash → Resource Integrity

21. Web Proxies

A web proxy can sit between a browser and a web application.

Browser
   ↕
Proxy
   ↕
Web Application

A penetration tester can use a proxy to:

Intercept requests
Inspect requests
Modify requests
Forward requests
Analyze responses

Web proxies are extremely useful during web application security testing.

22. Burp Suite

Burp Suite is a popular web application security testing platform.

It includes a proxy that can intercept HTTP/HTTPS traffic.

Editions
Community Edition
Professional Edition
Common Uses
Intercepting requests
Modifying parameters
Examining cookies
Testing authentication
Testing authorization
Analyzing application behavior
Easy Memory

Burp Suite → Web Proxy + Security Testing

23. OWASP ZAP

OWASP ZAP = Zed Attack Proxy

It is a free and open-source web application security testing tool.

Features
Web proxy
Automated scanning
Fuzzing
Vulnerability detection

ZAP can help security testers identify and investigate vulnerabilities in web applications.

Easy Memory

ZAP → Proxy + Scan + Fuzz

24. Burp Suite vs OWASP ZAP
Feature	Burp Suite	OWASP ZAP
Web Proxy	✅	✅
Intercept Traffic	✅	✅
Modify Requests	✅	✅
Automated Scanning	✅	✅
Fuzzing	✅	✅
Free Version	Community Edition	Free/Open Source
Important Question

Which tools can intercept and forward web traffic?

Answer:

Burp Suite
OWASP ZAP
25. Directory and File Enumeration Tools

These tools help discover files and directories on web servers.

Gobuster
Written in Go
Directory/file enumeration
Uses wordlists
FFUF
Written in Go
Fast web fuzzer
Web enumeration and fuzzing
Feroxbuster
Written in Rust
Web reconnaissance
Fuzzing
DirBuster
Discovers directories and files on web servers
Easy Memory

Gobuster → Enumeration

FFUF → Fast Fuzzing

Feroxbuster → Recon + Fuzzing

DirBuster → Directory Discovery

26. Wordlists

A wordlist is a file containing many possible values that a tool can test.

Example
admin
login
dashboard
backup
uploads
api
config

Enumeration tools use these values to determine whether corresponding resources exist.

Easy Memory

Wordlist → List of Possible Names

27. OWASP WSTG

OWASP WSTG = OWASP Web Security Testing Guide

It is an important reference for web application security testing.

It Provides Guidance On
Web application security testing
Vulnerability identification
Testing methodologies
Security recommendations
Vulnerability mitigation
Easy Memory

WSTG → Web Security Testing Guide

28. ZAP + WSTG

The module demonstrates combining:

OWASP WSTG → Methodology & Reference

with:

OWASP ZAP → Practical Testing & Scanning

Together They Help Testers
Identify potential vulnerabilities.
Investigate findings.
Understand vulnerabilities.
Determine underlying causes.
Identify appropriate mitigation.
Easy Memory

WSTG = How to Test

ZAP = Tool to Test

29. Important Vulnerability Concepts
Information Exposure

Sensitive information is accidentally exposed to unauthorized users.

Improper Error Handling

Application errors reveal information that may help attackers.

Hard-Coded Credentials

Credentials are directly embedded into source code.

Race Condition

An attacker exploits timing or an incorrect sequence between operations.

API Security Issues

APIs may lack:

Authentication
Authorization
Input validation
Other necessary security controls
Parameter Tampering

An attacker modifies application parameters to change application behavior.

Lack of Code Signing

Software authenticity and integrity cannot be reliably verified.

30. Important CWE Numbers
CWE	Vulnerability
CWE-615	Information Exposure Through Comments
CWE-798	Use of Hard-coded Credentials
CWE-227	API Abuse
Easy Memory

CWE-615 → Comments

CWE-798 → Credentials

CWE-227 → API Abuse

31. Tools to Remember
Tool	Main Purpose
Burp Suite	Web proxy and security testing
OWASP ZAP	Proxy, scanning and fuzzing
Gobuster	Directory/file enumeration
FFUF	Fast web fuzzing
Feroxbuster	Web reconnaissance/fuzzing
DirBuster	Directory enumeration
Radamsa	Fuzzing/test-data generation
32. High-Value Concepts
Shift Left

Security testing should begin early in the development lifecycle.

Hidden ≠ Secure

A hidden HTML field can still be modified by the client.

Error Messages

Detailed errors can reveal useful information to attackers.

Hard-Coded Credentials

Passwords, API keys and secrets should not be embedded directly into source code.

Race Condition

Think:

Timing + Incorrect Sequence + Small Exploitation Window

API Testing

Do not inspect only URLs.

Capture and analyze the complete HTTP request.

Fuzzing

Think:

Unusual/Malformed Input → Application Response

Code Signing

Think:

Digital Signature → Authenticity + Integrity

SRI

Think:

Cryptographic Hash → External Resource Integrity

Web Proxy

Think:

Browser → Proxy → Server

A proxy allows security testers to intercept, inspect and modify HTTP/HTTPS traffic.
