5.2 Wireless Vulnerabilities
1. Why Wireless Security Is Important
Wi-Fi signals can travel outside a building, allowing attackers to potentially attempt access to an organization's internal network from outside.
A secure wireless network should protect:
•	Wireless access 
•	Authentication 
•	Internal resources 
•	Sensitive business data 
Important Idea
Gaining access to Wi-Fi can potentially provide an attacker with a path toward internal systems.
________________________________________
2. Rogue Access Point (Rogue AP)
A Rogue AP is an unauthorized wireless access point installed by an attacker.
Purpose
The attacker attempts to trick users into connecting to the malicious access point.
Example
Attacker
   ↓
Rogue AP
   ↓
Victim
   ↓
Internal Network
A Rogue AP can potentially provide the attacker with a backdoor into the network.
________________________________________
3. Evil Twin Attack
An Evil Twin is a Rogue AP configured to look like a legitimate wireless network.
Example
Real Network: corp-net
Fake Network: corp-net
The attacker makes the fake network appear legitimate.
DNS Spoofing
An attacker may use DNS spoofing to redirect users to:
•	A cloned website 
•	A fake captive portal 
•	A malicious page 
The victim may believe they are still using the legitimate network.
Captive Portal
A captive portal is a webpage commonly used on public Wi-Fi for:
•	Login 
•	Accepting terms and conditions 
•	Providing an email address 
•	Viewing advertisements 
Attackers can create fake captive portals to steal information.
Remember
Evil Twin = Fake Wi-Fi that looks like the real Wi-Fi.
________________________________________
4. Disassociation / Deauthentication Attack
An attacker attempts to disconnect a legitimate wireless client from its real access point.
Possible Purposes
•	Create a wireless DoS 
•	Force the victim toward an Evil Twin 
•	Obtain authentication information 
Protection
802.11w Management Frame Protection (MFP) helps protect against spoofed management frames used in deauthentication attacks.
________________________________________
5. Wireless Reconnaissance Tools
Airmon-ng
Airmon-ng is part of the Aircrack-ng suite.
It is used to put a wireless adapter into monitor mode and observe wireless activity.
Airodump-ng
Airodump-ng can be used to:
•	Sniff wireless traffic 
•	Discover wireless networks 
•	Identify SSIDs 
•	Identify channels 
•	Observe connected clients 
•	View encryption information 
Important Terms
SSID: Name/identifier of a wireless network.
BSSID: Identifier associated with a particular wireless access point.
ESSID: In the source material, this essentially identifies the same network as the SSID.
________________________________________
6. Hidden SSID
Some organizations configure access points so that the SSID is not actively broadcast.
However:
A hidden SSID does not make the network invisible.
When a legitimate client begins the association process with the access point, a wireless sniffer may be able to capture the SSID.
Key Point
Hidden SSID ≠ Strong Security
________________________________________
7. Preferred Network List (PNL) Attack
Devices often maintain a Preferred Network List (PNL) containing trusted wireless networks.
A device may automatically attempt to connect to networks in this list.
An attacker can listen for requests from clients and impersonate one of their preferred networks.
Risk
The victim may connect to the attacker's wireless device, potentially allowing traffic to be monitored or manipulated.
________________________________________
8. Wireless Signal Jamming
Jamming means generating interference or noise on wireless frequencies.
Goal
To create a:
DoS (Denial of Service)
This may cause:
•	Partial wireless disruption 
•	Complete wireless disruption 
•	Clients disconnecting from access points 
Modern wireless systems may include features that help detect such attacks.
________________________________________
9. War Driving
War driving means moving around an area while searching for wireless networks.
An attacker can collect information about nearby Wi-Fi networks.
War Flying
A similar concept, but wireless networks are searched from:
•	Aircraft 
•	Drones 
•	Other UAVs 
________________________________________
10. WEP and IV Attacks
Initialization Vector (IV)
An IV is information used with encryption during wireless communication.
WEP uses a 24-bit IV.
The IV is transmitted in plaintext, which creates security weaknesses.
WEP
WEP is obsolete and insecure.
WEP:
•	Uses RC4 
•	Uses 24-bit IVs 
•	Is vulnerable to IV-related attacks 
•	Can have its PSK recovered after sufficient traffic is collected 
Bottom Line
Never rely on WEP for modern wireless security.
________________________________________
11. WPA / WPA2 Attacks
WPA and WPA2 are stronger than WEP, but they can still have vulnerabilities.
One important attack involves capturing the WPA four-way handshake.
General Concept
Find Client
     ↓
Authentication/Connection
     ↓
Handshake Captured
     ↓
PSK May Be Attacked
A captured handshake can potentially be subjected to password-guessing or brute-force techniques, depending on password strength.
Important
WPA is not vulnerable to the same IV attacks as WEP.
________________________________________
12. KRACK Attack
KRACK = Key Reinstallation Attack
KRACK affects certain implementations of WPA/WPA2.
Depending on the device and configuration, the vulnerability can allow an attacker to reinstall a previously used encryption or integrity key.
Potential Consequences
•	Traffic interception 
•	Traffic decryption attempts 
•	Traffic manipulation 
•	Replay of previously observed traffic 
Most vendors released patches, and WPA3 addresses these vulnerabilities.
________________________________________
13. WPA3 Vulnerabilities
WPA3 is stronger than WPA/WPA2, but:
No security protocol is completely perfect.
The material mentions vulnerabilities involving:
•	Side-channel attacks 
•	Downgrade attacks 
•	DoS conditions 
•	Fragmentation attacks 
Dragonfly Handshake
WPA3 introduced a new handshake called the Dragonfly handshake.
Important
WPA3 is not automatically immune to every possible attack.
________________________________________
14. WPS PIN Attack
WPS = Wi-Fi Protected Setup
WPS was designed to make wireless setup easier.
Some WPS implementations allow repeated PIN attempts, making them vulnerable to brute-force attacks.
The material mentions Reaver as a tool associated with WPS attacks.
________________________________________
15. KARMA Attack
KARMA = Karma Attacks Radio Machines Automatically
KARMA involves creating a Rogue AP.
The attacker listens for probe requests from wireless devices.
If a device searches for a particular SSID, the attacker can create an AP using that SSID.
The device may then connect to the attacker's AP.
Simple Idea
Victim searches for known Wi-Fi
             ↓
Attacker imitates it
             ↓
Victim connects
KARMA can therefore be used against the Preferred Network List (PNL) concept.
________________________________________
16. Wireless Fragmentation Attack
Wireless fragmentation attacks can be used against WEP-configured devices.
The attack can obtain PRGA (Pseudo-Random Generation Algorithm) elements.
The PRGA material can potentially be used to generate packets for wireless injection.
Important Distinction
A fragmentation attack does NOT directly recover the WEP key.
Instead, it obtains PRGA material that can be used for further wireless attacks.
________________________________________
17. Credential Harvesting
Credential harvesting means obtaining users' credentials.
Wireless environments can be used for credential harvesting through:
•	Rogue APs 
•	Evil Twins 
•	Fake captive portals 
•	DNS spoofing 
A victim may connect to a fake network and see a fake login page.
Victim connects to fake network
            ↓
Fake login page appears
            ↓
Victim enters credentials
            ↓
Credentials are captured
Tools Mentioned
•	Ettercap — can spoof DNS replies 
•	SET (Social-Engineer Toolkit) — can assist with social engineering/credential-harvesting activities 
________________________________________
18. Bluejacking
Bluejacking is a Bluetooth attack in which an attacker sends unsolicited messages to a nearby Bluetooth device.
It can involve a vCard containing information such as:
•	Name 
•	Address 
•	Phone number 
•	Email 
•	Website URL 
It is mainly described as a form of Bluetooth spam.
Remember
Bluejacking = Sending unwanted information/messages
________________________________________
19. Bluesnarfing
Bluesnarfing is more serious than Bluejacking.
It involves unauthorized access to information stored on a Bluetooth-enabled device.
Potentially targeted information includes:
•	Contacts 
•	Calendar 
•	Emails 
•	Text messages 
•	Pictures 
•	Videos 
It may also expose the device's IMEI.
Easy Difference
Attack	Main Idea
Bluejacking	Sends unwanted messages
Bluesnarfing	Steals/accesses information
________________________________________
20. Bluetooth Low Energy (BLE) Attacks
BLE (Bluetooth Low Energy) is widely used by IoT devices.
BLE can be vulnerable to:
•	On-path attacks 
•	Message manipulation 
•	DoS attacks 
•	Fingerprinting attacks 
An attacker may potentially manipulate communication between devices that believe they are communicating with legitimate systems.
________________________________________
21. RFID Attacks
RFID = Radio-Frequency Identification
RFID uses electromagnetic fields to identify and track tags containing stored information.
Types of RFID
Passive RFID
•	Gets energy from the RFID reader 
•	Usually has a shorter range 
Active RFID
•	Has its own power source 
•	Can operate over longer distances 
Common RFID Attacks
RFID Information Theft
An attacker can use an RFID reader to silently read information.
RFID Cloning
An attacker copies an RFID tag and creates a duplicate.
Skimming
A hidden reader/skimmer may be placed near an RFID reader.
NFC Amplification
Amplified antennas can potentially extend the range of NFC-related attacks.
________________________________________
22. Password Spraying
Password spraying is a credential attack in which an attacker tries a common password against many usernames.
Example
user1 → CommonPassword
user2 → CommonPassword
user3 → CommonPassword
The attacker avoids repeatedly attacking a single account.
Credential Stuffing — Do Not Confuse Them
Credential stuffing uses previously leaked username/password combinations from other breaches.
Attack	What Is Tried?
Password Spraying	One common password against many accounts
Credential Stuffing	Previously leaked username/password pairs
Easy Memory
Spraying → One password, many accounts
Stuffing → Old leaked credentials
________________________________________
23. Exploit Chaining
Sophisticated attacks often use multiple vulnerabilities together.
Instead of relying on a single vulnerability:
Vulnerability 1
       ↓
Vulnerability 2
       ↓
Vulnerability 3
       ↓
Compromise
This is called exploit chaining.
A vulnerability that appears to have low risk by itself can sometimes become much more serious when combined with another weakness.
