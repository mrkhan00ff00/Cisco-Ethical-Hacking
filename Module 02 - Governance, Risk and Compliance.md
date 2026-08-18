# Module 2: Governance, Risk, Compliance and Ethical Hacking

## 2.1 Governance, Risk & Compliance (GRC)

### What is GRC?

* **Governance:** The rules, policies, and responsibilities used to manage an organization's security.
* **Risk:** The possibility of loss or damage caused by a threat.
* **Compliance:** Following laws, regulations, and security standards.

### What Must a Penetration Tester Understand Before Testing?

Before starting a penetration test, the tester should know:

* What is the target?
* What is the scope?
* What is allowed to be tested?
* What is not allowed to be tested?
* When will testing take place?
* Who is responsible?
* Who should be contacted in an emergency?
* What are the budget and time limitations?
* What are the technical restrictions?

> **Golden Rule:** Never perform penetration testing without written permission.

---

## Important Compliance Frameworks

### PCI DSS — Payment Card Industry Data Security Standard

PCI DSS protects credit and debit card information.

If an organization stores, processes, or transmits payment card data, PCI DSS may be relevant.

#### Important Points

* **PAN (Primary Account Number)** is a major factor in determining PCI DSS applicability.
* Cardholder data must be properly protected.
* Sensitive authentication data should not be stored after authorization.

### HIPAA

HIPAA protects healthcare information.

Its main focus includes:

* **Electronic Protected Health Information (ePHI)**

It applies to organizations such as healthcare providers, health plans, and healthcare clearinghouses.

### GDPR

GDPR protects individuals' personal data and privacy in the EU.

The main idea is to give users greater control over their personal data.

### GLBA

GLBA protects customer information in the financial sector.

It applies to financial services organizations regardless of size.

### NIST SP 800-57

NIST SP 800-57 provides guidelines for cryptographic key management.

---

## Quick Revision

| Framework          | Main Purpose                   |
| ------------------ | ------------------------------ |
| **PCI DSS**        | Payment/card data security     |
| **HIPAA**          | Healthcare/ePHI protection     |
| **GDPR**           | Personal data and privacy      |
| **GLBA**           | Financial customer information |
| **NIST SP 800-57** | Cryptographic key management   |

### Easy Way to Remember

* **PCI → Cards**
* **HIPAA → Healthcare**
* **GDPR → Privacy**
* **GLBA → Finance**
* **NIST 800-57 → Keys**

---

## Legal Concepts

A penetration tester must understand contracts and legal documents.

### SLA — Service-Level Agreement

Defines service performance expectations.

Examples include:

* Timeline
* Quality
* Response time
* Performance requirements

### SOW — Statement of Work

Defines exactly:

**What work must be performed and what must be delivered in the project.**

### MSA — Master Service Agreement

Defines the overall/general business terms between a client and a service provider.

### NDA — Non-Disclosure Agreement

Prevents confidential information from being shared with unauthorized people.

### Confidentiality

Keeping sensitive information secret and protected.

### Disclaimer

Clarifies the limitations and responsibilities associated with a report.

For example, a penetration testing report does not mean that the system is completely free of vulnerabilities.

---

## Most Important Contract Requirement

For penetration testing, there must be:

**Proper written authorization + authorization from the appropriate signing authority.**

If third-party systems or cloud providers may be affected by the testing, their permission may also be required.

---

## Local Restrictions and Technical Constraints

A penetration tester must follow the laws of the relevant country and the organization's rules.

Before testing, identify:

* Which systems can be tested?
* Which systems are out of scope?
* Which tools are allowed?
* Which attacks are prohibited?
* Is there a risk of damaging production systems?
* Could tests such as SQL injection affect the database?
* What restrictions does the cloud provider have?

> **Important Rule:** If it is not in scope → **Do not test it.**

---

# 2.2 Rules of Engagement & Scope

## Rules of Engagement (RoE)

A Rules of Engagement (RoE) document defines:

**The conditions and rules under which a penetration test will be conducted.**

It commonly includes:

* Allowed and disallowed tests
* Testing timeline
* Testing hours
* Target systems
* Communication process
* Emergency contacts
* Testing limitations

### Example

If a client says:

> **"Testing can only be performed between 10 PM and 2 AM."**

This becomes part of the Rules of Engagement.

---

## Scope / In-Scope Assets

Scope means exactly which systems, networks, applications, and assets are authorized for testing.

The scope may include:

* IP addresses/ranges
* Domains
* Subdomains
* Wireless SSIDs
* Web applications
* APIs
* Servers
* Network devices
* Cloud resources

---

## Technical Information

The client may provide the penetration tester with:

* API documentation
* Network topology
* System architecture diagrams
* Wireless SSIDs
* Source code
* Credentials
* SDKs
* Example requests

---

## API Documentation

A penetration tester may receive different types of API documentation, such as:

* SOAP
* Swagger
* WSDL
* GraphQL
* WADL

These documents help the tester understand the available API endpoints and functions.

---

## Scope Creep

Scope creep occurs when the scope of a project continuously increases without proper agreement.

### Example

**Original agreement:**

> "Only the website will be tested."

**Later, the client says:**

> "Test the internal network and Wi-Fi as well."

If these were not included in the original scope, this may be considered scope creep.

### Solution

Use:

**Change management + a new or updated SOW**

---

## How to Validate the Scope

Before starting testing:

1. Ask questions to the client.
2. Review the contract/SOW.
3. Verify in-scope assets.
4. Identify out-of-scope assets.
5. Confirm testing restrictions.
6. Identify stakeholders and emergency contacts.
7. Establish communication channels.
8. Arrange a secure method for transferring data.

---

## Penetration Testing Is a Point-in-Time Assessment

This is a very important concept.

A penetration test shows the security posture of an environment at the time the test was performed.

### Example

* **January:** 1,000 systems tested
* **Next year:** 1,100 systems tested
* **Later:** 2,200 systems tested

Vulnerabilities can change because:

* New systems are added.
* New software is installed.
* New vulnerabilities are discovered.
* Configurations change.

Therefore:

> **One penetration test does not provide permanent security.**

**Regular testing and remediation are necessary.**

---

# Unknown vs Known Environment

## Unknown-Environment Testing

Previously called **Black Box Testing**.

The penetration tester receives very limited information about the target.

Usually, this may include:

* Domain names
* IP addresses
* Basic target information

### Purpose

To test the environment from the perspective of an external attacker.

The tester performs reconnaissance and gradually discovers information about the target.

> **Remember:** Unknown = Less information

---

## Known-Environment Testing

Previously called **White Box Testing**.

The penetration tester receives considerably more information about the target.

Examples include:

* Network diagrams
* Configurations
* Source code
* Architecture
* Credentials

### Purpose

To perform a deeper assessment of specific systems and security areas.

---

## Quick Comparison

| Unknown Environment           | Known Environment              |
| ----------------------------- | ------------------------------ |
| Limited information           | More information               |
| External attacker perspective | Insider/authorized perspective |
| More reconnaissance required  | Less initial reconnaissance    |
| Usually broader               | Can be more targeted           |

---

# 2.3 Ethical Hacking Mindset

## Ethical Hacker vs Malicious Hacker

The main difference is **authorization and ethics**.

### Ethical Hacker

Identifies security weaknesses with legal permission.

### Malicious Hacker

Performs unauthorized access or exploitation.

---

## Professionalism & Integrity

A professional penetration tester should follow these principles:

### 1. Follow the Scope

Only test systems that are authorized.

### 2. Maintain Confidentiality

Client information such as:

* Data
* Credentials
* Vulnerabilities
* Reports

must not be shared with unauthorized people.

### 3. Perform Proper Background Checks

The skills and trustworthiness of the penetration-testing team should be verified.

### 4. Use Tools Carefully

Not every tool is allowed in every penetration-testing engagement.

### 5. Limit Invasiveness

Avoid attacks that can unnecessarily cause:

* Downtime
* Data loss
* Service disruption

### 6. Report Criminal Activity

If evidence of a previously compromised system is discovered during testing, the appropriate stakeholder should be informed.

---

# Risk Concepts

## Risk Tolerance

Risk tolerance is the amount of risk an organization is willing to accept.

### Example

A company may know that a minor risk exists but decide to accept it because of the business benefits.

---

## Risk Management

Risk management is the process of identifying, assessing, and controlling risks.

A basic flow is:

**Identify → Assess → Decide → Mitigate/Accept → Monitor**

### Risk Acceptance

The organization decides:

> **"We will accept this risk."**

### Risk Mitigation

Steps are taken to reduce the risk.

### Example

**Vulnerable software → Patch/update → Risk reduced**
