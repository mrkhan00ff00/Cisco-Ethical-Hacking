Module 1 — Ethical Hacking and Penetration Testing
1.1 Understanding Ethical Hacking and Penetration Testing
1.1.1 Ethical Hacking
An ethical hacker is a security professional who thinks like an attacker to find weaknesses in systems, networks, and applications. The purpose is to identify vulnerabilities before malicious attackers can exploit them.
The most important difference between ethical and malicious hacking is authorization and intent.
•	Ethical hacking: Authorized and performed to improve security. 
•	Malicious hacking: Unauthorized and performed with harmful or illegal intent. 
Scope and Authorization
Before starting a penetration test, the tester must have permission from the system owner.
The scope defines:
•	What systems can be tested. 
•	What systems cannot be tested. 
•	Which IP addresses, domains, applications, or networks are included. 
•	Which testing activities are allowed. 
A penetration tester must stay within the approved scope.
Vulnerability Disclosure
If a security researcher discovers a vulnerability, it should be responsibly reported to the vendor or system owner.
Finding a vulnerability is not the problem. Using it without authorization to access a system is unethical and potentially illegal.
Penetration Testing
Penetration testing is an authorized security assessment in which a tester:
1.	Identifies security weaknesses. 
2.	Attempts to validate or exploit those weaknesses. 
3.	Determines the possible impact. 
4.	Reports the findings. 
5.	Helps the organization fix the weaknesses. 
________________________________________
1.2 Why Penetration Testing Is Important
Organizations use security controls such as:
•	Firewalls 
•	Antivirus 
•	Anti-malware 
•	IPS 
•	VPN 
•	WAF 
•	Defense-in-depth 
However, simply installing security controls does not prove that they are effective.
Penetration testing helps determine whether an attacker can bypass these defenses and reach protected systems or data.
Attack Surface
The attack surface is the collection of possible entry points an attacker could target.
It can change when an organization:
•	Adds new systems. 
•	Deploys new applications. 
•	Changes network configurations. 
•	Opens new services. 
•	Updates infrastructure. 
Because the attack surface changes over time, security testing should be performed regularly.
Key point: Security controls should be tested, not simply trusted.
________________________________________
1.3 Threat Actors
A threat actor is an individual or group that can perform malicious activities against a target.
A penetration tester needs to understand different threat actors because penetration testing may simulate real-world attacker behavior.
Common Threat Actors
Organized Crime
Organized cybercrime groups are usually financially motivated and may use attacks such as:
•	Ransomware 
•	Data theft 
•	Other attacks that can generate financial profit 
Hacktivists
Hacktivists are attackers motivated primarily by political, social, or ideological goals.
State-Sponsored Attackers
These attackers are associated with or supported by governments and may target organizations for intelligence, strategic, or political purposes.
Insider Threats
An insider threat comes from someone who already has legitimate access to an organization's systems or information.
________________________________________
1.4 Penetration Testing Methodology
Penetration testing should follow a structured methodology rather than being performed randomly.
A methodology helps the tester:
•	Stay organized. 
•	Maintain proper scope. 
•	Avoid missing important areas. 
•	Document the testing process. 
•	Produce consistent and defensible results. 
Scope Creep
Scope creep occurs when testing expands beyond the originally approved scope.
A defined methodology helps reduce this risk.
________________________________________
1.5 Types of Penetration Testing
Network Infrastructure Testing
Network infrastructure testing evaluates the security of network components such as:
•	Switches 
•	Routers 
•	Firewalls 
•	IPS devices 
•	AAA servers 
The goal is to identify weaknesses that could allow an attacker to compromise the network.
Wireless Testing
Wireless penetration testing evaluates the security of wireless networks.
It may involve testing:
•	Wireless authentication. 
•	Wireless encryption. 
•	Security configurations. 
•	Possible methods of bypassing wireless protections. 
Physical Security Testing
Physical penetration testing evaluates whether an attacker could gain unauthorized physical access to a facility.
It can test:
•	Gates 
•	Fences 
•	Guards 
•	Physical security controls 
Social Engineering Testing
Social engineering tests how people respond to attacks rather than only testing technology.
Common examples include:
•	Phishing emails 
•	Phone-based attacks 
•	Fake websites 
•	SMS attacks 
The goal should be to identify weaknesses in the organization's security awareness and improve defenses.
________________________________________
1.6 Penetration Testing Perspectives
The amount of information provided to a penetration tester can change the testing approach.
Unknown-Environment Testing
The tester receives very limited information about the target.
For example:
•	Domain names 
•	IP addresses 
The goal is to simulate an external attacker who must perform reconnaissance and discover information about the target.
Known-Environment Testing
The tester has significant information about the target environment before testing begins.
This allows the tester to perform a more informed security assessment.
Partially Known-Environment Testing
The tester receives some information about the target but not everything.
This provides a balance between the unknown-environment and known-environment approaches.
________________________________________
1.7 Bug Bounty Programs
A bug bounty program allows security researchers to report vulnerabilities to organizations.
Organizations may provide:
•	Recognition 
•	Financial rewards 
The main purpose is to find vulnerabilities before malicious attackers can exploit them.
Bug bounty programs are different from traditional penetration tests, but both focus on discovering security weaknesses.
________________________________________
1.8 Penetration Testing Methodologies and Standards
Important methodologies and standards include:
MITRE ATT&CK
A knowledge base that organizes real-world attacker tactics and techniques.
OWASP WSTG
A guide for testing the security of web applications and web services.
NIST SP 800-115
Provides guidance for conducting technical security testing and assessments.
OSSTMM
A methodology for performing structured security testing.
PTES
Provides a structured approach for conducting penetration tests.
ISSAF
Provides guidance for performing information systems security assessments.
A penetration tester should understand multiple methodologies because no single methodology is perfect for every engagement.
________________________________________
1.9 Building a Penetration Testing Lab
A penetration tester needs a safe environment for learning and testing tools.
Testing should be performed on:
•	Your own systems. 
•	Intentionally vulnerable machines. 
•	Simulated environments. 
•	Systems for which you have explicit permission. 
Kali Linux
Kali Linux is a Linux distribution that contains many penetration testing and security tools.
Other security-focused Linux distributions mentioned in the course include:
•	Parrot OS 
•	BlackArch 
Virtualization
A penetration testing lab can be created using:
•	VirtualBox 
•	VMware 
A simple lab can contain:
Kali/Parrot VM
       |
Virtual Network
       |
Vulnerable VM
A host-only network can allow the virtual machines to communicate with each other while keeping the test traffic isolated from the physical network.
Lab Isolation
A testing environment should be isolated from real networks whenever possible.
Important practices include:
•	Use a closed network. 
•	Use virtual machines. 
•	Provide sufficient hardware resources. 
•	Use intentionally vulnerable targets. 
•	Avoid exposing vulnerable systems directly to the Internet. 
________________________________________
1.10 Penetration Testing Tools
The tools used depend on what is being tested.
Network Testing
Tools can be used for:
•	Traffic analysis. 
•	Traffic manipulation. 
•	Network device testing. 
•	Firewall testing. 
•	IPS testing. 
Wireless Testing
Tools can be used for:
•	Testing wireless encryption. 
•	Testing wireless security. 
•	Deauthentication testing. 
•	On-path/MITM testing. 
Web Application Testing
Tools can be used for:
•	Vulnerability scanning. 
•	Intercepting HTTP/HTTPS traffic. 
•	Manual web testing. 
•	Testing vulnerabilities such as SQL injection. 
Vulnerability Scanning
Vulnerability scanners can help identify:
•	Outdated software. 
•	Misconfigurations. 
•	Known vulnerabilities. 
Mobile Application Testing
Mobile testing requires tools for examining:
•	Mobile applications. 
•	Backend APIs. 
•	Supporting services. 
Fuzzing
Fuzzing tests how an application or protocol behaves when it receives unexpected or unusual input.
________________________________________
1.11 Recovery and Backups
Penetration testing can sometimes break or modify a system.
Therefore, a tester should always have a recovery plan.
Snapshots
Virtual machines allow testers to create snapshots before testing.
If something breaks, the previous state can be restored quickly.
Backups
For systems that cannot be virtualized, maintain a complete backup so the system can be restored if testing causes problems.
Key point: Before performing potentially destructive testing, make sure the environment can be restored.
________________________________________
1.12 Kali Linux Basics
Kali Linux provides both a graphical interface and a command-line shell.
Basic Linux knowledge is important because many penetration testing tools are operated from the terminal.
pwd
The pwd command displays the current working directory.
For the Kali user in the course environment:
pwd
Output:
/home/kali
