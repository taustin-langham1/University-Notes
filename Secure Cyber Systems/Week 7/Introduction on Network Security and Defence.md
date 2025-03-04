**[Week 7 Slides](file:///home/thomas/Downloads/lecture-7.pdf)**

- lecture outline 
	- Types of Network Attacks
	- Firewall
	- Intrusion detection/intrusion prevention
	- IPSec, SSL/TLS
	- VPN


## Types of Network Attacks

**Passive Attacks**

- make use of information, but not affect system resources
- Eavesdropping or monitoring transmissions of information
	- release message contents
	- Traffic analysis
- Relatively hard to detect, but easier to prevent

**Active Attacks**

- Alter system resources or operation. 
- four main types:
	- Masquerade: pretend to be someone else
	- Replay: re transmission of captured information
	- Modification: change message contents 
	- Denial of service: reduce the availability of resources
- Relatively hard to prevent, but easier to detect 

#### Passive: Message Collection and Analysis

*Example:* if Bob sends sensitive information (e.g., company secrets) from his office to Alice's office. Darth can intercept and collect these messages.

#### Active Attack: Masquerade / Spoofing 

*Example:* Darth is pretending to be bob, darth sends a message to alice that says "please transfer me all you moneys to bank account 123456, Love Bob XoX"

#### Active Attack: Replay

*Example:* Today. bob sends message to alice "Please leave your laptop on your office desk at lunch time" - tomorrow darth replays the same message and steals alice's laptop

#### Active Attack: Modification / Manipulation

*Example:* Bob sends a message to alice in the finance department 
"please pay darth 100gbp for the extra work he did" darth intercepts and modifies the message before it reaches alice by changing 100 to 10,000



## Virus vs. Worm 

- *A worm* is a standalone malicious program capable of self replicating and spreading through networks, typically without needing to attach itself to other files or programs
	- Examples:
		- Conflicker
		- WannaCry
- *A virus* is a type of malicious code that attaches itself to other programs or files and requires user interaction to activate and spread

### Differences 


![[Pasted image 20250226110824.png]]

## Famous examples of attacks:

**Stuxnet 2010**


**Mirai Botnet 2016**


**Colonial Pipeline Ransomware Attack 2021**




# Network Security Mechanisms 

## Network Security Solutions

- FIrewall
	- Security perimeter Control
	- Network Segmentation/Segregation
- Intrusion Detection / Prevention Systems (IDS/IPS)
- IPSec
- SSL/TLS
- Virtual Private Network (VPN)


## Firewall

 - firewall filters information that is sent and received from outside the network
	 - it is software that resides on the networks gateway
- Restricts access between a protected network and other networks
- Protects internal networks from users attempting to use unauthorised internet services

#### Types of Firewall

**Packet Filtering firewall**
- Applies a set of rules to incoming IP packets
- Forwards and discards packets
- Can be configured to filter packets going in both directions

**Stateful Inspection Firewall**
- Not only inspect individual packets, but also track connection states
- determines whether a packets is the start, a part or not a part of a connection
- The firewall uses the ongoing record, or state table, to make informed decisions about which traffic to allow or block

**Proxy Firewall**
- Acts as a middleman between the client and the server, proxying all traffic
- It processes requests by establishing a connection to the requested service on behalf of the user
Features:
- provides deep inspection and can filter application layer content
- has low performance and may become a network bottleneck

**Application Layer Firewall**

- is designed to protect a website or application from various types of attacks by checking application level traffic
- can be configured to support only specific applications or specific features of an application
	- able to detect if an unwanted protocol is attempting to bypass the firewall on an allowed port
- One type of application firewall is a web application firewall which is specifically designed for HTTP applications 


## Intrusion Detection


- it is a kind of network security technology that aims to monitor abnormal activities or potential security threats in a network or system and issue alarms in a timely manner

- intrusion detection system (IDS) is a tool to implement this technology, its main function is to identify and report possible attack behaviours or policy violations

### Main functions

*Monitoring:* Analyse network traffic or system activity in real time

*Detection:* identify know attack patterns (signature detection) or abnormal behaviour (anomaly detection)

*Alert:* Alert administrators when potential threats are detected

*Logging:* Record detected activities for subsequent analysis forensics

### Types of Intrusion Detection:
#### (based on deployment methods)

**Network Based IDS (NIDS):** Deployed in the network to monitor network traffic

**Host-Based IDS (HIDS):** Deployed on a single host to monitor system logs, file changes, and user activities

**Hybrid IDS:** Combines the merits from NIDS and HIDS.

#### (based on detection methods)


**Signature-based detection:** identify threats by matching them to known attack paterns - signatures -

**Anomaly-based detection:** by establishing a baseline of normal behavior, identify anomalous activity that deviates from that baseline 

**Specification-based Detection:** uses predetermined universal profiles based on "accepted definitions of benign activity" developed by security managers



## Intrusion Detection vs Prevention


• Intrusion Detection System
(IDS): Only monitors and alarms,
does not actively prevent attacks

• Intrusion Prevention System (IPS):
When a threat is detected, it actively
takes blocking or isolation measures.



## Internet protocl security (IPSec)


- a protocol suite for protecting IP communications, ensuring data security during transmission by providing encryption, authentication, and integrity protection at the network layer

- **IPSec** is widely used in scenarios such as virtual private networks (VPNs), remote access, and enterprise network connections

- some services provided:
	- establishing mutual authentication
	- negotiation of cryptographic keys - data confidentiality 
	- data integrity 
	- replay protection
	- automated management of cryptographic keys and security associations

- **IPSec Protocols**

- Authentication Header (**AH**)
	- verifies that the data comes from a trusted source and hasn't been changed

- Encapsulating Security Payload (**ESP**)
	- Performes authentication and also encrypts the data

 - Security Assocation (**SA**)
	- is the basis of IPSec communication and defines the security parameters (such as encryption algorithm, key, and protocol mode) used by both communicating parties


#### IPSsec Operation Modes

**Transport Mode:**
- operates primerily on the payload (data) of the original packet. only the payload of the IP packet is encrypted, and the IP header remains unchanged 
- suitable for end-to-end communication (such as host to host)

**Tunnel Mode:**
- original packet encapsulated into a new one, payload is original packet
- suitable for network-to-network or host-to-network communications (such as VPN)

**IPSec - Communication initiaion**

- Ipsec used cryptographic keys, which can be created and shared using a process called **IKE (Internet key exchange)**


- **IKE** is responsible for key management, ensuring that both communicating parties can securely exchange encryption keys and other security parameters to establish a secure IPSec connection


**IKE Phase-1**

initially the sender will exchange the proposals for security services (*encryption algorithms, authentication algorithm, hash function, ect*) the sender and reciever will agree on a collection of parameters that the two devices use

**IKE Phase-2**

the devices between the sender and receive will choose which protocol (*Authentication header or Encapsulation Security Protocol*) and which algorithm to use)


## Secure Sockets Layer


*Secure Sockets Layer (SSL)* is an encryption protocol used to protect network communications. It has been replaced by the more secure **Transport Layer Security (TLS)**

- referring to **SSL/TLS** technology

- **SSL/TLS** is mainly used to establish an encrypted connection between the client and the server to ensure the confidentiality, integrity and identity authentication of data during transmission


### SSL Handshake Protocol

**The handshake protocol**
- negotiates the encryption to be used
- establishes a shared session key
- authenticates the server 
- authenticates the client (optional)
- Completes the session establishment

- after the handshake, application data is transmitted securely 


## Transport Layer Security 

**An encryption protocol used to protect network communication securely**

**Core functions**

*Data Encryption:* Encryption algorithms (such as AES) are used to protect the confidentiality of data and prevent eavesdropping

*Data Integrity:* hash algorithms (such as SHA-256) are used to ensure that data has not been tampered with during transmission

*Identity authentication:* the identity of the server (and client) is verified through digital certificated to prevent man-in-the-middle attacks


