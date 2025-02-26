**[Week 6 Slides](file:///C:/Users/langh/Downloads/Lecture-6.pdf)**

- basic concept of Network Security 
- Network models
- Common network Attacks
- Security Landscape with Advanced Persistent Threats (APT)

- describe both OSI model and TCP/IP model
- describe the common network attacks
- understand the changing security landscape

#### Security Overview

network security is any activity designed to protect the usability and integrity of your network and data

- it includes both hardware and software technologies
- it targets a variety of threats
- it stops them from entering or spreading on your network
- effective network security manages access to the network#

![[Pasted image 20250219110435.png]]


# Network Security 

- is concerned with **confidentiality integrity** and **availability of network resources**

- several mechanisms have been designed to provide these properties at different levels of the network model
- these mechanisms can work together or separately to provide some or all of the desired security properties


## Network Types:

- **Local area network (LAN)**
- **Personal area network (PAN)**
- **Wireless local area network (WLAN)**
- **Campus area network (CAN)**
- **Metropolitan area network (MAN)**
- **Wide area network (WAN)**


## Network Models:

**OSI MODEL**

- the open systems interconnection (OSI) model is a conceptual framework that divides network communications functions into seven layers
- also known as OSI/ISO model
- It provides a universal language for computer networking, so diverse technologies can communicate using standard protocols or rules of communication

![[Pasted image 20250219111035.png]]

## Seven Layers of the OSI model


- **Physical layer**
	- The physical layer refers to physical communication medium and the technologies to transmit data across that medium. At its core, data communication is the transfer of digital and electronic signals through various physical channels like fiber-optic cables, copper cabling and air
- **Data link layer**
	- The data link layer refers to the technologies used to connect two machines across a network where the physical layer already exists. it manages data frames, which are digital signals encapsulated into data packets
- **Network layer**
	- The network layer is concerned with concepts such as routing, forwarding, and addressing across a dispersed network or multiple connected networks of nodes or machines
- **Transport Layer**
	- The primary focus of the transport layer is to ensure that data packets arrive in the right order, without losses or errors, or can be seamlessly recovered if required. common protocols include TCP, UDP, ect. TCP is commonly used where all data must be intact (e.g., file share) whereas UDP is used when retaining all packets is less critical
- **Session layer**
	- The session layer is responsible for network coordination between two separate applications in a session. a session manages the beginning and ending of a one-to-one application connection and synchronization conflicts
- **Presentation layer**
	- The presentation layer is primarily concerned with the syntax of data itself for applications to send and consume
- **Application layer**
	- The application layer is concerned with the specific type of application itself and its standardized communication methods

## Security aspects

- **data link layer is considered to be the weakest link in the OSI model** because LANs traditionally were under admin control of a single org. where all persons devices were trusted

- **Network layer data is transferred in the form of packets via logical network paths in an ordered format controlled by the network layer.** That mean packet is associated with this layer, which includes IP header, TCP header, data.


## Internet Model or TCP/IP Model

**Internet or Network Layer**

****

- this layer parallels the functions of OSI's network layer. it defines the protocols which are responsible for the logical transmission of data over the entire network

**IP:** stands for internet protocol. responsible for delivering packets to destinations by looking at the IP address in the packet headers

**ICMP:** stands for the **Internet Control Message Protocol**. it is encapsulated within IP datagrams and is responsible for providing hosts with information about network problems

**ARP:** stands for **Address Resolution Protocol** its aim is to find the hardware address of a host from a known IP address


**Transport Layer**

****
The TCP/IP transport layer protocols exchange data receipt acknowledgments
and retransmit missing packets to ensure that packets arrive in order and
without error. End-to-end communication is referred to as such.

**TCP (Transmission Control Protocol):**  is connection-oriented, meaning that sender and receiver firstly need to
establish a connection based on agreed parameters; they do this through three-
way handshake procedure

**UDP (User datagram protocol):** is a connectionless protocol meaning that messages are sent without
negotiating a connection and that UDP does not keep track of what it has sent.


**Application Layer**

****

• The Application Layer in the TCP/IP model combines the functions of three
layers from the OSI model: the Application, Presentation, and Session layers.
It is responsible for end-to-end communication and error-free delivery of
data.

**HTTP and HTTPS a)** HTTP stands for Hypertext transfer protocol. It is used by the
World Wide Web to manage communications between web browsers and
servers. **b)** HTTPS stands for HTTP-Secure. It is a combination of HTTP with
SSL(Secure Socket Layer).

**SSH**: stands for **Secure shell.**  It is a terminal emulations software similar to
Telnet. It sets up a secure session over a TCP/IP connection.



## TCP Three-Way Handshake

- TCP provides reliable communication with something called Positive
Acknowledgement with Re-transmission(PAR) where a device using PAR resend
the data unit until it receives an acknowledgement.


# Common Network Attacks

#### **IP SPOOFING**

is an attack at the network layer (IP)
is executed by sending manipulated datagrams from the attacker to the target system, using the sender address of an authorized system

#### **ARP SPOOFING**

- is a type of attack in which a malicious actor sends falsified ARP (Address resolution protocol) messages over a local area network

- this results in the linking of an attacker's MAC address with the IP address of a legitimate computer on the computer or server on the network

- an attacker sends unsolicited "response packets" with manipulated IP-MAC association
#### **TCP SEQ NUM PREDICTION**

- A TCP sequence prediction attack is an attempt to predict the sequence number used to identify the packets in a TCP connection, which can be used to counterfeit packets. The attack hopes to correctly guess the sequence number to be used by the sending host

#### **DENIAL OF SERVICE (DOS)** 

• A denial-of-service (DoS) attack is a type of cyber attack in which a malicious actor
aims to render a computer or other device unavailable to its intended users by
interrupting the device's normal functioning.
• The aim is to harm the availability of a service.
• DoS attacks typically function by overwhelming or flooding a targeted machine with
requests until normal traffic is unable to be processed, resulting in denial-of-service to
addition users.
• A DoS attack is characterized by using a single computer to launch the attack

#### **DISTRIBUTED DENIAL OF SERVICE (DDoS)**

• It is a malicious attempt to disrupt the normal traffic of a targeted server, service or
network by overwhelming the target or its surrounding infrastructure with a flood of
Internet traffic.
• DDoS attacks achieve effectiveness by utilizing multiple compromised computer
systems as sources of attack traffic.
• When a victim’s server or network is targeted by the botnet, each bot sends requests
to the target’s IP address, potentially causing the server or network to become
overwhelmed.
#### **DNS SPOOFING**



#### **NETWORK SNIFFING**

- Sniffing attack in context of network security, corresponding to theft or interception of data by capturing the network traffic

## Traditional Security Landscape


- **Basic Threats**
	- Pranks 
	- Ransomeware
	- spyware
	- trojans
	- backdoors/rootkits
- **Basic delivery mechanisms**
	- **viruses** replicates itself by modifying other computer programs and inserting its own code
	- **worms** replicates itself in order to spread to other computers
	- **phishing** attackers send scam emails (or text messages) that contain links to malicious websites
	- **Software vulnerabilities**
		 **SQL-injections:** used to attack data-driven applications, in which malicious SQL statements are
			inserted into an entry field for execution
		 **Cross-Site Scripting:** enables attackers to inject client-side scripts into web pages viewed by other users



**One two three**

hey i said this 




