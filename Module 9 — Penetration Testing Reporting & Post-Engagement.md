# Module 9 — Penetration Testing Reports, Remediation & Communication

# 9.1 Written Penetration Testing Reports

A **penetration testing report** is the final deliverable that communicates:

* **What was tested**
* **What was discovered**
* **The associated risk**
* **How the client should address the findings**

---

## 1. Know Your Audience

A report may be read by different audiences.

### Executives / C-Suite

**Need:**

* Clear high-level summary
* Major findings
* Business impact
* Overall risk

### IT / Security Teams

**Need:**

* Technical details
* Evidence
* Remediation information

### Developers

Need enough technical information to:

* Reproduce vulnerabilities
* Understand the cause
* Fix application security issues

> **Important:** The report should be **clear, professional, respectful, and understandable** for its intended audience.

---

# 2. Main Report Sections

| Section               | Purpose                                                |
| --------------------- | ------------------------------------------------------ |
| **Executive Summary** | High-level scope, major findings, and overall risk     |
| **Scope Details**     | Systems, applications, networks, and boundaries tested |
| **Methodology**       | How the penetration test was conducted                 |
| **Findings**          | Vulnerabilities discovered and supporting evidence     |
| **Remediation**       | Recommended fixes                                      |
| **Conclusion**        | Overall assessment                                     |
| **Appendix**          | Supporting technical information                       |

---

# 3. CVE and CVSS

## CVE

**CVE = Common Vulnerabilities and Exposures**

CVE is a catalog of **publicly known vulnerabilities**.

Each vulnerability receives an identifier and description.

---

## CVSS

**CVSS = Common Vulnerability Scoring System**

CVSS is a standardized system for rating **vulnerability severity**.

### Scores

**0–10**

It helps organizations prioritize vulnerabilities.

---

## CVSS Metric Groups

### Base

Represents the fundamental characteristics of the vulnerability.

### Temporal

Represents characteristics that can change over time.

### Environmental

Considers the organization's specific environment and threat surface.

> **Key Point:** Environmental metrics provide **organization-specific context**.

---

# 4. Secure Report Distribution

Penetration testing reports contain sensitive information and should generally be treated as **highly classified**.

### Best Practices

* Produce only the required number of copies.
* Define the distribution list.
* Identify individual copies.
* Maintain a distribution log.
* Deliver copies securely.
* Encrypt reports during electronic transfer.
* Store electronic copies on secure systems.
* Securely delete tester copies after delivery according to the agreed process.

> **Rule:** Distribute reports on a **need-to-know basis**.

---

# 5. Note Taking

Documentation should begin **during the penetration test**, not after it.

### Record

* Findings
* Commands and tools used
* Steps taken
* Screenshots
* Tool output
* Relevant evidence
* Videos when necessary

Good note-taking makes the final report **more accurate and easier to prepare**.

---

# 6. Dradis

**Dradis** is a penetration-testing collaboration and reporting tool.

### It Can

* Import results from various security tools
* Organize findings
* Help create reports
* Export information in formats such as **CSV, HTML, and PDF**

---

# 7. Root Cause Analysis

A scanner's output alone is **not enough**.

A penetration tester should:

1. **Validate the finding.**
2. **Understand the actual environment.**
3. **Determine the business impact.**
4. **Correlate multiple findings.**
5. **Identify the root cause.**
6. **Assign an appropriate risk level.**
7. **Recommend remediation.**

### Example

An old FTP service may not contain a known vulnerability. However, if it is:

* Internet-accessible
* Used by employees
* Storing sensitive information

then it may still represent a **significant security risk**.

> **Important:** False positives can cause organizations to waste time and money fixing problems that do not actually exist.

---

# 9.2 Analyzing Findings and Recommending Remediation

Finding vulnerabilities is only **one part** of a penetration test.

A good penetration tester should also provide **appropriate remediation recommendations**.

Security controls can be divided into **four major categories**.

---

# 1. Technical Controls

Technology-based security protections.

### Examples Include

* System hardening
* Input sanitization
* Query parameterization
* Multifactor authentication
* Password encryption
* Process-level remediation
* Patch management
* Key rotation
* Certificate management
* Secrets management
* Network segmentation
* Microsegmentation

---

## Microsegmentation

**Microsegmentation** controls communication at the application, VM, or container level rather than relying only on traditional VLANs.

It commonly follows a **Zero Trust** approach:

> Communication is denied unless an explicit policy allows it.

This can help limit **lateral movement**.

---

# 2. Administrative Controls

Administrative controls involve **policies, procedures, management decisions, and organizational processes**.

---

# 3. Operational Controls

Operational controls involve security activities and procedures performed by people or operational teams.

### Time-of-Day Restrictions, Mandatory Vacations, and Training

* **Time-of-day restrictions** — limit when users are allowed to access systems.
* **Mandatory vacations** — require employees to take time off, which can help detect suspicious activities.
* **User/security training** — teaches users how to follow secure practices.

---

## Security Awareness vs. Training

### Security Awareness

> Reminds users about proper and secure behavior.

### Security Training / Education

> Teaches users specific security skills and knowledge.

---

# 4. Physical Controls

Physical controls protect **buildings, rooms, equipment, and other physical resources**.

### Examples

* Access control vestibules
* Biometric controls
* Video surveillance

---

# Four Major Control Categories

Remember these four categories:

> **Technical + Administrative + Operational + Physical**

These are the four major categories of security controls that can be considered when recommending remediation.

### Example

**Missing HttpOnly Cookie Attribute →** Recommend enabling the **HttpOnly flag** on cookies.

---

# 9.3 Communication During Penetration Testing

Communication is very important throughout a penetration test.

A penetration tester should communicate regularly with the client instead of waiting until the final report is completed.

---

# Important Contacts

## Primary Contact

* The main person responsible for the penetration test.
* Usually the person who hired the testing team or someone officially assigned by them.

## Technical Contacts

* IT or security staff who can help the penetration tester during testing.

## Emergency Contacts

* People who should be contacted if a serious or unexpected emergency happens.

---

# Communication Triggers

Some situations require **immediate communication** according to the agreed rules.

## 1. Critical Findings

Critical vulnerabilities may need to be reported **immediately** instead of waiting for the final report.

## 2. Status Reports

The client may request regular updates about the progress of the penetration test.

## 3. Evidence of Previous Compromise

If the tester discovers evidence that a **real attacker may have already compromised the organization**, the client should be informed immediately.

The tester should **not wait until the final report**.

---

# False Positives and False Negatives

## True Positive

A real security or malicious event occurs and is correctly identified.

## True Negative

Normal activity occurs and is correctly identified as normal.

## False Positive

The system reports malicious activity, but there is actually **no attack**.

### Problem

Too many false positives can overwhelm security teams and make it harder to notice real threats.

## False Negative

A real malicious activity occurs, but the security system **fails to detect it**.

---

# Goal Reprioritization

During penetration testing, new discoveries may cause the client to change priorities.

For example:

* An application that was previously low priority becomes critical.
* The client asks the tester to investigate a newly discovered risk.
* Some planned testing activities become less important.

Therefore, **communication and change management** are important for controlling **scope creep**.

### Scope Creep

> **Scope creep** means that the testing work gradually expands beyond the originally agreed scope.

---

# Findings Should Be Reproducible

A technical finding should contain enough information for the responsible team to understand and reproduce the vulnerability.

For example, an **SQL injection** finding should ideally include:

* Relevant HTTP request and response
* Description of the vulnerability
* Evidence showing that the vulnerability is real
* Screenshots when necessary
* Recommended remediation

Any sensitive information shown in screenshots should be **redacted**.

### Redaction

**Redaction** means hiding or removing sensitive information before sharing it.

---

# 9.4 Post-Report Delivery Activities

Delivering the report does **not** mean that the penetration test is immediately finished.

After the report is delivered and the findings are presented, the tester must clean up the testing environment and complete other post-engagement activities.

---

# 1. Post-Engagement Cleanup

Penetration testing can leave behind different types of artifacts, such as:

* User accounts
* Files
* Tools
* Shells
* Test data
* Configuration changes
* Other temporary artifacts

These should be removed according to the **agreed rules**.

---

## Important Cleanup Tasks

### Tester-Created Credentials

* Remove accounts and credentials created during testing.

### Shells

* Remove shells created on compromised systems.

### Tools

* Remove tools that were installed or left on systems during testing.

### Test Data

* Remove data that was created or inserted during testing.

> **Important:** The client or system owner should ideally verify that cleanup has been completed.

---

# 2. Additional Post-Report Activities

## Client Acceptance

The client formally accepts or signs off on the final penetration-testing report.

---

## Lessons Learned

The testing team and client review:

* What went well
* What went wrong
* What could be improved
* How future penetration tests can be better managed

---

## Follow-Up Actions / Retesting

After the client fixes the vulnerabilities, the tester may perform a **retest**.

### Purpose of Retesting

To verify that the vulnerabilities have actually been **fixed**.

---

## Attestation of Findings

This is the formal confirmation or documentation of the penetration-testing findings and results.

---

## Data Destruction

Any sensitive client data collected during testing should be **securely destroyed** according to the agreed process.

---

# Module 9 — Quick Revision

| Concept                        | Easy Memory                      |
| ------------------------------ | -------------------------------- |
| **Penetration Testing Report** | Findings + Risk + Remediation    |
| **Executive Summary**          | High-Level Business View         |
| **CVE**                        | Vulnerability Identifier/Catalog |
| **CVSS**                       | Vulnerability Severity Score     |
| **Base Metrics**               | Fundamental Characteristics      |
| **Temporal Metrics**           | Changes Over Time                |
| **Environmental Metrics**      | Organization-Specific Context    |
| **Need-to-Know**               | Secure Report Distribution       |
| **Dradis**                     | Reporting & Collaboration        |
| **Root Cause Analysis**        | Find the Actual Cause            |
| **Technical Controls**         | Technology-Based Security        |
| **Administrative Controls**    | Policies & Management            |
| **Operational Controls**       | Security Operations              |
| **Physical Controls**          | Physical Protection              |
| **Microsegmentation**          | Limits Lateral Movement          |
| **Security Awareness**         | Reminds Users                    |
| **Security Training**          | Teaches Skills                   |
| **False Positive**             | Alert, But No Attack             |
| **False Negative**             | Attack, But No Detection         |
| **Scope Creep**                | Testing Expands Beyond Scope     |
| **Redaction**                  | Hide Sensitive Information       |
| **Retesting**                  | Verify Fixes                     |
| **Cleanup**                    | Remove Testing Artifacts         |
| **Data Destruction**           | Securely Destroy Client Data     |

---

# Module 9 — Key Takeaways

### Penetration Testing Report

> **Tested → Findings → Risk → Remediation**

### Know Your Audience

> **Executives → Business Impact**
> **IT/Security → Technical Details**
> **Developers → Reproduction + Fix**

### CVE vs CVSS

> **CVE → What Vulnerability?**
> **CVSS → How Severe?**

### Root Cause Analysis

> **Validate → Understand → Correlate → Find Root Cause → Remediate**

### Four Security Control Categories

> **Technical + Administrative + Operational + Physical**

### Communication

> **Critical Finding → Communicate Immediately**

### False Positive vs False Negative

> **False Positive → No Attack, Alert Generated**
> **False Negative → Attack Exists, No Alert**

### Scope Creep

> **Testing Expands Beyond Agreed Scope**

### Reproducible Findings

> **Evidence + Details + Reproduction + Remediation**

### Post-Engagement

> **Cleanup → Client Acceptance → Lessons Learned → Retesting → Data Destruction**
