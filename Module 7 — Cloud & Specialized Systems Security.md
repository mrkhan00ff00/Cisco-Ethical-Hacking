7.1 Module Overview

Module 7 focuses on security risks associated with cloud technologies and specialized systems.

Topics Covered
Cloud computing models
Cloud attack vectors
Credential harvesting
Privilege escalation
Account takeover
Metadata service attacks
Misconfigured cloud assets
Denial-of-Service and resource exhaustion
Malware injection
Side-channel attacks
Mobile security
IoT security
IoT protocols
Management interfaces
Virtual machine vulnerabilities
Container and Kubernetes security
Main Idea

Modern infrastructure is no longer limited to traditional servers.

Organizations now use:

Cloud services
Mobile devices
IoT devices
Virtual machines
Containers
Kubernetes

Each technology introduces its own security risks.

Part 1 — Cloud Computing
7.2 What Is Cloud Computing?

Cloud computing provides computing resources and services over a network instead of requiring organizations to maintain everything locally.

Cloud Resources Can Include
Computing power
Storage
Applications
Databases
Networking
Development platforms

Cloud environments are powerful and flexible, but they can be difficult to secure because resources can be created quickly and may sometimes be forgotten or incorrectly configured.

7.3 Why Cloud Security Is Important

Cloud environments may contain:

Sensitive information
Application code
User accounts
Databases
Credentials
Intellectual property

A compromised cloud environment can potentially result in:

Data theft
Data exfiltration
Data deletion
Privacy violations
Account compromise
Service disruption
Key Point

Cloud security follows many traditional IT security principles, but cloud environments introduce additional complexity.

7.4 CapEx vs OpEx
CapEx — Capital Expenditure

Money spent on long-term physical infrastructure.

Examples:

Purchasing servers
Purchasing networking equipment
Building data centers
OpEx — Operating Expenditure

Ongoing operational costs.

Examples:

Paying for cloud computing resources
Paying for storage
Paying for cloud services
Key Point

Cloud computing commonly allows organizations to move from CapEx toward OpEx.

7.5 Advantages of Cloud Computing

Important advantages include:

Distributed storage
Scalability
Resource pooling
Access from almost anywhere
Measured services
Automated management
7.6 Essential Characteristics of Cloud Computing
1. On-Demand Self-Service

Users can provision resources whenever they need them.

2. Broad Network Access

Services can be accessed through networks using different types of devices.

3. Resource Pooling

Cloud resources are shared among multiple customers or users.

4. Rapid Elasticity

Resources can quickly scale up or down according to demand.

5. Measured Service

Cloud resource usage can be monitored and measured.

7.7 Cloud Deployment Models
Public Cloud

Cloud infrastructure is available for public use.

Private Cloud

Cloud infrastructure is dedicated to a particular organization.

It may exist:

On-premises
In a dedicated provider environment
Community Cloud

Cloud infrastructure is shared by multiple organizations with common requirements.

Hybrid Cloud

A hybrid cloud combines two or more cloud environments.

Example:

Private Cloud + Public Cloud

It may also combine cloud infrastructure with on-premises infrastructure.

7.8 Cloud Service Models

There are three major cloud service models.

IaaS — Infrastructure as a Service

Provides infrastructure resources such as:

Virtual machines
Storage
Networking

The customer has significant control over the infrastructure.

PaaS — Platform as a Service

Provides a platform for developing and running applications.

The cloud provider manages much of the underlying infrastructure.

SaaS — Software as a Service

Provides a complete application to users.

Users generally access the software through the internet rather than managing the underlying infrastructure.

Easy Memory

IaaS → Infrastructure

PaaS → Platform

SaaS → Software

Part 2 — Cloud Attack Types
7.9 Credential Harvesting

Credential harvesting means stealing authentication information.

This can include:

Usernames
Passwords
Tokens
PINs
Session credentials

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

7.10 MFA and Credential Harvesting

MFA = Multi-Factor Authentication

MFA provides additional authentication factors beyond a password.

It significantly improves protection against ordinary password theft.

However, some attacks may attempt to steal session information, so MFA alone is not a complete defense against every possible attack.

Important Idea

Password + MFA ≠ Absolute Security

Organizations should also consider:

Phishing-resistant authentication
Session protection
Monitoring
User awareness
7.11 SSO and Federated Authentication
SSO — Single Sign-On

SSO allows users to access multiple services using a common authentication mechanism.

Federated Authentication

Federated authentication allows authentication between different organizations or services using trusted identity relationships.

These technologies improve usability, but they can become attractive targets because compromising an identity provider may provide access to multiple connected services.

7.12 Privilege Escalation

Privilege escalation occurs when an attacker gains more privileges than they are authorized to have.

Example:

Normal User → Administrator

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

7.13 Account Takeover

An account takeover occurs when an attacker gains control of a legitimate user or application account.

After compromising an account, an attacker may attempt to access:

Sensitive information
Cloud resources
Applications
Databases
Indicators of Account Takeover

Organizations can monitor for:

Unusual login locations
Repeated failed login attempts
Lateral phishing emails
Suspicious OAuth, SAML, or OpenID Connect connections
Abnormal file sharing
Unusual downloads
7.14 Metadata Service Attacks

Cloud platforms may provide metadata services that applications use to obtain temporary credentials and configuration information.

These services can contain highly valuable information.

For example, a cloud virtual machine may request temporary credentials through its metadata service.

Why Attackers Target Metadata Services

If an attacker can improperly access a metadata service, they may obtain:

Access keys
Secret credentials
Temporary tokens
Instance information
Configuration information
Important Security Concept

Cloud applications should prevent untrusted users or applications from accessing sensitive metadata-service endpoints.

7.15 Misconfigured Cloud Assets

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

7.16 Resource Exhaustion and DoS
DoS — Denial of Service

A DoS attack attempts to make a service unavailable to legitimate users.

DDoS — Distributed Denial of Service

A DDoS attack uses multiple systems to generate attack traffic against a target.

Important Measurements
Measurement	Meaning
bps	Bits per second; commonly associated with overwhelming network bandwidth
pps	Packets per second; often targets network equipment and infrastructure
rps	Requests per second; often targets application or web servers
7.17 Direct-to-Origin Attack

A Direct-to-Origin (D2O) attack attempts to discover the original server's IP address behind a CDN or proxy.

Normal Flow
User
 ↓
CDN / Proxy
 ↓
Origin Server
If the Origin Is Discovered
Attacker
 ↓
Origin Server

The attacker may then be able to bypass protections provided by the CDN or proxy.

7.18 CDN

CDN = Content Delivery Network

A CDN uses geographically distributed servers or proxies to help provide:

Better performance
High availability
Distributed content delivery
7.19 Cloud Malware Injection

In a cloud malware injection attack, an attacker attempts to introduce a malicious application or instance into a cloud environment.

If successful, the malicious instance may provide a foothold for further attacks.

Possible Consequences
Backdoors
Data theft
Eavesdropping
Data manipulation
Covert communication
7.20 Side-Channel Attacks

A side-channel attack obtains information from indirect characteristics of a system rather than directly exploiting its intended functionality.

Possible Information Sources
Timing
Power consumption
Electromagnetic emissions
Sound
Hardware behavior

Attackers may attempt to extract:

Credentials
Cryptographic keys
Sensitive information
Spectre and Meltdown

Spectre and Meltdown are examples of processor vulnerabilities associated with side-channel attacks.

They affected various processor architectures and could potentially expose sensitive information.

Part 3 — Mobile Security
7.21 Mobile Device Attacks

Mobile applications and devices have unique security risks.

One important technique is reverse engineering.

Reverse engineering involves analyzing a compiled mobile application to understand:

Application structure
Application logic
APIs
Embedded information
Potential weaknesses

Attackers may use reverse engineering to discover vulnerabilities or compromise mobile platforms.

7.22 Common Mobile Vulnerabilities
Insecure Storage

Sensitive information may be stored insecurely on a device.

Examples:

Passwords
Tokens
Personal data
Passcode and Biometric Vulnerabilities

Weak authentication mechanisms or incorrect biometric implementations can allow unauthorized access.

Certificate Pinning Problems

Certificate pinning helps an application verify that it is communicating with the expected certificate or endpoint.

Incorrect implementation can weaken application security.

Vulnerable Components

Applications may contain outdated or vulnerable third-party libraries or components.

Excessive Permissions

Applications should not receive more permissions than necessary.

This relates to the Principle of Least Privilege.

Example: A game should not unnecessarily have access to sensitive device resources.

Business Logic Vulnerabilities

An application may technically function as designed, but the design itself may allow unintended or insecure behavior.

7.23 Mobile Security Tools
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
Important Tool Matches
ApkX → Decompiles APK files
Postman → API testing and development
Drozer → Android security testing
Frida → Dynamic instrumentation
Ettercap → On-path attacks
MobSF → Automated mobile application/malware analysis
Part 4 — IoT Security
7.24 What Is IoT?

IoT = Internet of Things

IoT includes internet-connected physical devices such as:

Sensors
Cameras
Smart devices
Industrial equipment
Gateways
Monitoring systems

IoT environments can include:

SCADA
IIoT
ICS
Smart home systems
Transportation systems
7.25 Why IoT Security Is Difficult

IoT environments are complicated because they often involve:

Different hardware
Different software
Legacy technologies
Multiple vendors
Multiple integrators
Different device limitations
Cloud services
Network gateways

There is no single security solution that works for every IoT environment.

Three Important Reasons
Legacy technologies
Multiple vendors and integrators
Disparate hardware and software
7.26 IoT Architecture

A simplified IoT architecture can be represented as:

Endpoints → Gateways/Fog → Cloud → Applications
Endpoints

The actual IoT devices or "things."

Gateways/Fog Layer

Intermediate devices such as:

Routers
Switches
Computing platforms
Cloud

Provides:

Storage
Processing
Other cloud services
Applications

Use collected information to provide business functionality.

7.27 Common IoT Protocols

Important IoT protocols include:

Wi-Fi
Bluetooth
Bluetooth Low Energy (BLE)
Zigbee
Z-Wave
LoRaWAN
Insteon
Modbus
Siemens S7comm
7.28 Bluetooth Low Energy (BLE)

BLE is widely used in:

Home devices
Medical equipment
Industrial devices
Government equipment
BLE Connection Establishment

Phase 1: Pairing and feature exchange

Phase 2: Short-term key generation

Phase 3: Transport-specific key distribution

BLE supports cryptographic functions including AES.

However, some devices may fail to implement encryption properly.

7.29 BLE Security Problems

Attackers may:

Scan BLE devices
Listen to advertisements
Identify poorly configured devices
Create fake or cloned BLE devices
Perform on-path attacks
Important Tools

Ubertooth One

Specialized hardware for Bluetooth/BLE research.

GATTacker

Can be used to test BLE implementations and perform on-path attacks.

BtleJuice

A framework for intercepting and manipulating BLE traffic.

7.30 IoT Security Considerations

IoT devices often have limited computing resources.

This creates a security challenge because some devices may not have sufficient resources to support strong security mechanisms.

For example, encryption may not be properly supported.

Other concerns include:

Availability
Data corruption
Data exfiltration
7.31 Common IoT Vulnerabilities
Insecure Defaults

Devices may ship with default:

Usernames
Passwords
Configurations

These should be changed.

Plaintext Communication

Data may be transmitted without encryption, potentially exposing sensitive information.

Hard-Coded Configurations

Important configuration information may be permanently embedded into devices or software.

Outdated Firmware

Old firmware may contain known vulnerabilities.

Devices should support security updates.

7.32 IoT Security Checklist

For networked IoT devices, verify that:

Default credentials have been changed.
Default configurations have been changed.
Firmware/software can be updated.
Communications support encryption.
Part 5 — IoT Management Interfaces
7.33 IPMI

IPMI = Intelligent Platform Management Interface

IPMI provides remote management and monitoring capabilities.

It can allow administrators to manage systems even when the operating system is:

Offline
Unresponsive
Powered off
7.34 BMC

BMC = Baseboard Management Controller

The BMC controls and monitors hardware.

Because it has significant access to the underlying hardware, compromising a BMC can be extremely serious.

An attacker who compromises a BMC could potentially:

Monitor the system
Reboot it
Modify system behavior
Install malicious software or implants
Key Idea

BMC access can be similar to physical access to the underlying system.

Part 6 — Virtual Machines
7.35 Virtual Machines

A virtual machine (VM) is intended to provide an isolated computing environment.

Multiple VMs can run on the same physical machine.

A hypervisor manages these virtual machines.

7.36 Type 1 Hypervisor

Also called a:

Bare-metal / Native Hypervisor

It runs directly on physical hardware.

Examples
VMware ESXi
Proxmox
Xen
Microsoft Hyper-V
7.37 Type 2 Hypervisor

Also called a:

Hosted Hypervisor

It runs on top of an existing operating system.

Examples
VirtualBox
VMware Workstation
VMware Player
Easy Memory Trick
Type 1 → Hardware → Hypervisor → VM


Type 2 → Operating System → Hypervisor → VM
7.38 VM Escape

A VM escape vulnerability allows an attacker to break out of a virtual machine's isolation.

Potential Impact
Compromised VM
      ↓
Hypervisor / Host
      ↓
Other VMs

This is particularly serious because the attacker may potentially access other virtual environments.

7.39 Hyperjacking

Hyperjacking involves compromising or controlling the hypervisor.

An attacker may attempt to introduce a malicious hypervisor or gain control of the existing hypervisor.

Because the hypervisor manages the virtual environment, compromising it can have widespread consequences.

Remember

VM Escape → Escape from the VM

Hyperjacking → Attack or control the hypervisor

7.40 VM Repository Vulnerabilities

Organizations often download ready-made VM images from repositories or marketplaces.

Attackers may upload:

Fake VMs
Impersonated VMs
Backdoored VMs
Malicious software

If an organization deploys a malicious VM image, the attacker may gain a foothold in the environment.

Security Lesson

Do not blindly trust downloaded VM images.

Use trusted sources and verify images whenever possible.

Part 7 — Container Security
7.41 Evolution of Computing

The module describes an evolution:

Physical Servers
       ↓
Virtual Machines
       ↓
Containers / Kubernetes
       ↓
Serverless

As flexibility increases, the attack surface can also change.

7.42 Containers

Containers package applications and their dependencies into isolated environments.

Examples
Docker
containerd
Rocket

Container environments can introduce vulnerabilities in:

Container images
Software inside containers
Host operating system
Container/host interaction
Runtime environment
Kubernetes/orchestration
7.43 Container Security Layers

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

7.44 Container Security Development Process

A secure container lifecycle can be viewed as:

Develop → Deliver → Deploy
Develop

Use:

Secure coding
Shift-left security
Security scanning
Deliver

Use:

Secure repositories
Secure user access
Image verification
Deploy

Use:

Runtime scanning
CIS Benchmarks
Security policies
Proper access controls
7.45 Containers Running as Root

Running containers with root privileges can be dangerous.

If an attacker exploits a vulnerability inside a container, excessive privileges can make the compromise more serious.

Principle

Avoid unnecessary root privileges.

This follows the Principle of Least Privilege.

7.46 CIS Benchmarks

CIS Benchmarks provide security configuration recommendations.

The module specifically mentions:

Docker
Kubernetes

They provide guidance for securely configuring these environments.

7.47 Container Security Tools
Grype

An open-source container vulnerability scanner.

Used to identify vulnerabilities in container images.

Clair

A container vulnerability analysis and scanning tool.

Dagda

An open-source static analysis tool for detecting:

Vulnerabilities
Trojans
Backdoors
Malware

in Docker images and containers.

kube-bench

Checks Kubernetes security configurations against the:

CIS Kubernetes Benchmark

kube-hunter

An open-source security tool designed to assess the security posture of Kubernetes clusters.

Falco

A threat-detection engine for Kubernetes and cloud-native environments.

7.48 Important Container Tool Matches

Remember:

Grype → Container vulnerability scanning
Dagda → Docker/container static analysis
kube-bench → CIS Kubernetes Benchmark
kube-hunter → Kubernetes security assessment
Falco → Threat detection
7.49 Supply Chain Attacks

Attackers can insert malicious code into legitimate-looking container images.

For example, malicious images can be uploaded to public repositories.

Organizations may download and deploy them without realizing they have been compromised.

Key Point

This is an example of a software supply-chain attack.
