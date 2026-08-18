

## 4.1 Pretexting, Approach & Impersonation

### What is Social Engineering?

Social engineering involves manipulating human psychology and trust to obtain information, access, or a specific action.

> **Important Idea:** In cybersecurity, the human user is often considered the weakest link.

### Elicitation

Elicitation means obtaining information from a person without directly asking for that specific information.

**Example:**

An attacker casually talks to an employee and obtains information about the company's systems through the conversation.

### Interrogation

In interrogation, an attacker asks the victim questions to gather information.

#### Open-Ended Questions

* Allow the victim to answer freely.
* May provide more information.

#### Closed-Ended Questions

* Give the attacker more control over the conversation.
* Limit the possible answer.
* Can be useful for directing or ending a conversation.

### Narrowing Approach

The attacker starts with broad questions and gradually moves toward more specific questions.

### What Does an Interrogator Observe?

An attacker may observe the victim's:

* Body language/posture
* Facial or color changes
* Eye and head movements
* Hand and foot movements
* Mouth/lip expressions
* Voice pitch and speaking rate
* Words, pauses, and speech patterns

---

### Pretexting

Pretexting means creating a fake story, situation, or identity to obtain information or access.

### Impersonation

Impersonation means pretending to be a trusted person or role.

**Examples:**

* Pretending to be an IT support employee
* Pretending to be a delivery person
* Pretending to be a company employee to obtain information

### Important Difference

* **Pretexting →** Using a fake scenario, story, or identity.
* **Impersonation →** Specifically pretending to be another person or role.

---

## Pharming

Pharming is an attack in which a victim is redirected from a legitimate website/resource to a malicious website.

### Possible Methods

* Host file modification
* DNS poisoning
* DNS server vulnerabilities
* Spoofed DNS replies

### Pharming Flow

```text
Legitimate Website
       ↓
Victim System Compromised
       ↓
Malicious Website
       ↓
Malware / Information Theft
```

### Prevention

* Keep software updated.
* Use anti-malware checks.
* Change default passwords on network devices.
* Be careful with suspicious websites and emails.

---

## Malvertising

Malvertising means placing malicious advertisements on trusted websites.

A user clicks the advertisement and may be redirected to a malicious website or malware.

### Pharming vs Malvertising

| Attack           | Main Idea                                                                 |
| ---------------- | ------------------------------------------------------------------------- |
| **Pharming**     | Redirecting a victim from a legitimate resource to a malicious resource   |
| **Malvertising** | Using a malicious advertisement on a trusted website to target the victim |

---

# 4.2 Social Engineering Attacks

Social engineering attacks primarily target human behavior.

## 1. Phishing

Phishing is the use of fake or trustworthy-looking emails, links, or attachments to convince a victim to provide sensitive information or open malicious content.

### Common Goals

* Steal usernames/passwords
* Install malware
* Obtain confidential information

### Example

```text
Fake Payment Confirmation Email
              ↓
        Link/Attachment
              ↓
         Victim Clicks
              ↓
    Credentials Stolen /
      Malware Installed
```

---

## 2. Spear Phishing

Spear phishing is targeted phishing aimed at a specific person, group, or organization.

The attacker first gathers information about the victim and then creates a more realistic message.

> **Remember:**
> **Phishing = Broad/General**
> **Spear Phishing = Specific Target**

---

## 3. Whaling

Whaling targets high-profile individuals.

### Targets May Include

* CEOs
* CFOs
* Executives
* Senior management

### Goals

* Obtain sensitive information
* Steal valuable credentials
* Gain financial or business access

> **Easy Memory:** Whaling → Big fish → Big target/executive

---

## 4. Vishing

**Vishing = Voice Phishing**

It involves using phone calls to obtain sensitive information from a victim.

An attacker may pretend to be:

* A bank employee
* A vendor
* A company representative

The attacker may also use caller ID spoofing.

### Possible Targets

* Financial information
* Account numbers
* Personal information

---

## 5. SMS Phishing / Smishing

SMS phishing, also called **smishing**, uses text messages to perform phishing attacks.

**Example:**

> "Your account has a problem. Click here to verify."

The victim opens the link → reaches a fake website → information may be stolen.

### Protection

Do not click unknown or unexpected SMS links.

If there is an issue with your bank, order, or account:

**Open the official website or application directly instead of clicking the link in the message.**

---

# 4.2 Social Engineering Attacks — Continued

## 6. USB Drop Key

A USB drop attack occurs when an attacker intentionally leaves USB drives in public or strategic locations.

### Basic Flow

```text
Victim finds USB
       ↓
Victim becomes curious and plugs it in
       ↓
Malicious file/malware may execute
```

### Key Point

The attacker exploits the victim's:

* Curiosity
* Helpful behavior
* Trust

---

## 7. Watering Hole Attack

A watering hole attack occurs when attackers target websites that their intended victims frequently visit.

### Basic Flow

```text
Identify websites frequently visited by victims
                    ↓
             Compromise website
                    ↓
            Inject malicious code
                    ↓
              Victim visits
                    ↓
             Redirect/exploit
                    ↓
             System compromise
```

The source material also explains this in the context of a pivot attack.

### Example

Employees frequently visit a gaming or community website.

The attacker:

1. Compromises the website.
2. Injects malicious JavaScript.
3. Waits for employees to visit.
4. Redirects them to a malicious exploit site.

### Prevention

* Keep anti-malware updated.
* Practice secure browsing.
* Provide security awareness training.
* Regularly scan and protect websites.
* Use secure virtual browsers where appropriate.

---

## Social Engineering Attacks — Quick Revision

| Attack                      | Main Idea                                                       |
| --------------------------- | --------------------------------------------------------------- |
| **Phishing**                | Fake email/link                                                 |
| **Spear Phishing**          | Targets a specific person/group                                 |
| **Whaling**                 | Targets executives/high-profile individuals                     |
| **Vishing**                 | Voice/phone-based phishing                                      |
| **SMS Phishing / Smishing** | Phishing through text messages                                  |
| **USB Drop Key**            | Malicious USB                                                   |
| **Watering Hole**           | Compromised website frequently visited by victims               |
| **Pharming**                | Redirecting a victim from a legitimate site to a malicious site |
| **Malvertising**            | Malicious advertisement                                         |

### Easy Memory

* **Phishing →** Fake email/link
* **Spear phishing →** Specific target
* **Whaling →** Executives
* **Vishing →** Voice
* **SMS phishing →** Text message
* **USB drop →** Malicious USB
* **Watering hole →** Compromised frequently visited website
* **Pharming →** Redirect
* **Malvertising →** Malicious advertisement

---

# 4.3 Physical Attacks

Cybersecurity is not limited to software and network security.

If an attacker gains physical access to a building or system, they may be able to bypass even strong cybersecurity controls.

## 1. Piggybacking

Piggybacking occurs when an unauthorized person enters a restricted area with an authorized person's permission or consent.

**Example:**

An employee opens a secure door and allows a known person to enter with them.

> **Piggybacking = With consent**

---

## 2. Tailgating

Tailgating occurs when an unauthorized person follows an authorized person into a restricted area without permission or consent.

### Very Important Difference

* **Piggybacking → With consent**
* **Tailgating → Without consent**

---

## Access Control Vestibule

An Access Control Vestibule, also known as a **mantrap**, is a small controlled area designed to restrict physical access.

### Basic Concept

```text
Door 1 → Controlled Space → Door 2
```

The second door normally opens only after the first door has closed.

It may be combined with:

* Proximity cards
* PINs
* Biometrics

### Security Control

An access control vestibule is a **preventive security control**.

---

## 3. Dumpster Diving

Dumpster diving means collecting private or sensitive information from garbage or recycling containers.

### Possible Information

* Paper documents
* Hard drives
* Removable media

### Prevention

Sensitive information should be properly destroyed using methods such as:

* Shredding
* Certified destruction
* Incineration where appropriate

---

## 4. Shoulder Surfing

Shoulder surfing means looking over someone's shoulder to obtain confidential information.

### Possible Targets

* Passwords
* Personally Identifiable Information (PII)
* PINs
* Information displayed on the screen

### Methods

An attacker may:

* Look directly from nearby.
* Use binoculars or a telescope.
* Use hidden cameras or microphones.

### Prevention

* Provide security awareness training.
* Use privacy/screen filters.
* Be careful when entering sensitive information in public places.

---

## 5. Badge Cloning

Badge cloning occurs when an attacker attempts to create a copy of an authorized building-access badge or card.

### Other Approaches

* Impersonating an employee
* Using a fake badge
* Social engineering

### Important Point

Attackers may also collect images of corporate badges from social media and use that information as part of an attack.

---

## Physical Attacks — Quick Revision

* **Piggybacking → WITH consent**
* **Tailgating → WITHOUT consent**
* **Dumpster Diving → Garbage**
* **Shoulder Surfing → Looking**
* **Badge Cloning → Copying a badge**

---

# 4.4 Social Engineering Tools

## 1. Social-Engineer Toolkit (SET)

**SET = Social-Engineer Toolkit**

It was developed by David Kennedy.

### Purpose

SET is a toolkit used to simulate and test social engineering attacks.

It can integrate with other frameworks such as Metasploit.

### SET Is Available By Default In

* Kali Linux
* Parrot Security

### SET Lab

A laboratory exercise may include:

1. Launching/exploring SET
2. Website cloning
3. Simulated credential harvesting
4. Viewing captured credentials

### Penetration Testing Use

A cloned version of an organization's website can be used in an authorized phishing simulation to test employee awareness.

> **Important:** Real-world use must remain within the authorized testing scope.

---

## 2. BeEF

**BeEF = Browser Exploitation Framework**

BeEF is a framework used for browser-based security testing and attacks.

According to the source material, BeEF can leverage XSS vulnerabilities to manipulate browsers.

### Examples

BeEF can be used for testing:

* Fake browser notifications
* Browser/user interaction monitoring
* Browser-based exploitation

### Lab Example

In a lab environment, BeEF can be used to:

* Create a fake browser notification.
* Redirect the user to a selected website when the notification is clicked.
* Demonstrate the ability to observe browser/user actions, including text-field entries.

---

## SET vs BeEF

| SET                                        | BeEF                           |
| ------------------------------------------ | ------------------------------ |
| Social engineering toolkit                 | Browser exploitation framework |
| Phishing/credential-harvesting simulations | Browser manipulation           |
| Website cloning                            | XSS/browser-based exploitation |
| Social engineering campaigns               | Compromised/hooked browsers    |

### Easy Memory

* **SET → Social Engineering**
* **BeEF → Browser Exploitation**

---

## 3. Call Spoofing Tools

### SpoofApp

* iOS/Android application
* Can spoof a phone number

### SpoofCard

Can provide features such as:

* Number spoofing
* Voice changing
* Call recording
* Background noises
* Sending calls directly to voicemail

### Asterisk

* Legitimate VoIP management tool
* Can be misused for caller-ID impersonation

### Easy Memory

* **SpoofApp → Number spoofing**
* **SpoofCard → Number + voice + recording + background noise**
* **Asterisk → VoIP + caller ID**

---

# 4.5 Methods of Influence

The core concept of social engineering is:

> **Understanding human behavior and motivation to persuade a victim to perform an action they would not normally perform.**

There are five important influence methods:

1. Authority
2. Scarcity
3. Social Proof
4. Likeness
5. Fear

---

## 1. Authority

The attacker creates an impression of authority, power, or confidence.

Authority may be:

* Organizational
* Legal
* Social

**Example:**

> "I am from the company's security department."

The victim may comply because they believe the attacker has authority.

---

## 2. Scarcity

The attacker presents something as having limited availability.

**Example:**

> "This offer is available for only 10 minutes."

The victim may make a quick decision without properly verifying the situation.

---

## 3. Social Proof

The attacker tells the victim that other people are already doing the same thing.

**Example:**

> "Other employees have already completed this form."

The victim may assume the action is normal and safe.

---

## 4. Likeness

The attacker creates a sense of similarity or connection with the victim.

Examples include:

* Similar interests
* Similar background
* Impersonating someone the victim admires

### Goal

To make the victim feel comfortable and cooperative.

---

## 5. Fear

The attacker creates fear of a dangerous or unpleasant consequence and pressures the victim to act quickly.

**Example:**

> "If you do not verify your account now, your account will be blocked."

Fear can cause the victim to act without properly verifying the request.
