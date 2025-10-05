### Intelligence gathering 

- phase of gathering information on, maps networks, as well as probing them for exploitable vulnerabilities to exploit them
- information gathered during this phase guides the rest of the penetration test


### Types of reconnaissance

- passive reconnaissance - gathering information on a target without their knowledge of your actions
	- e.g., using the internet to research a target


- active reconnaissance - gathering information on a target where the potential exists that your actions will be seen by the target
	- e.g., port scanning the target domains network looking for hosts and open services


## Passive Reconnaissance and Open-Source Intelligence

### Open source Intelligence


OSINT is intelligence that is produced publicly

the action of searching for publicly available information via the internet or "open-sources"
build an understanding of the organization, its employees, and relations to other organizations

https://osintframework.com/

- news broadcasts
- public request data
- paywalled data
- social media
- pastebin

no specialist tools/techniques required
can be used for social engineering
can include passwords/names/ip-addresses


#### infrastructure data collection

- ip address range
- ip address of specific systems
- device types
- operating systems
- services


#### fingerprint employees

- names
- roles
- relationships
- physical location
- contact details
- social media accounts


#### websites

- source code
	- comments
	- libraries
	- contact details
	- script types

- examine cookies
	- software in use
	- script types
- archived versions
- website mirroring

#### email headers


- obtaining email addresses
	- querying the domains email server
	- organizations website
- information from an email (explore the headers)
	- ip address of the sender
	- date and time
	- mail server

## Passive Network Sniffing

### Terminology

- sniffing - the act of capturing network traffic for analysis, replay, or other means
- Sniffer - software or hardware captures packets off the network
- SPAN / Mirror Port - must be configured on a switch. this sends a copy of all traffic out this port to the sniffer
- TAP - hardware device, similar to a phone tab, but in a network cab
- packet capture - act of capturing the entire packet or packet headers for analysis
	- this is done by sniffing
	- packet analyzers
		- wireshark (ethereal)
		- netwitness
	- Network debugging tools
		- TCPDump/WinDump
- Promiscuous mode - network card mode in which the host listens to all traffic on the network, not just what is destined or addressed only to itself


##### Packet sniffers - how do they work?


- Ethernet hardware ignores all traffic it encounters unless the destination MAC address matches it own
- packet sniffer deliberately reads all the traffic, instead of ignoring it
	- this allows sniffer to see all traffic on the network segment to which they are attached
- For this to work, sniffer must be located within the same network block as the network it is intended to sniff
	- though sniffer can be anywhere within that book

##### shared vs switched ethernet 

- switched ethernet 
	- in this formation, machines are connected to a switch
		- switch maintains MAC table, and keeps track of each computer MAC address and the physical port it is connected to 
-  packets are not broadcast, but sent to specific machine for which they are intended
- more secure than shared, though not completely secure
- sniffing can still occur using techniques like ARP spoofing, where MAC address of gateway is spoofed and all traffic is then routed through the machine running the sniffer

##### Passive Sniffing

- capturing traffic in a hub environment
- usually sniffer is placed in "promiscuous mode" and listens only


## Active Reconnaissance


#### Network Scanning

- the process of actively probing remote networks to discover live hosts and their open ports

#### Active network sniffing

- packets captured in a switch infrastructure or where the attacker is actively sending network traffic
- requires the sniffer to send packets to solicit a response, capture response, and potentially poison receiving hosts and/or infrastructure devices with the intent of receiving packets addressed to other hosts
- examples
	- ARP Poisoning
	- MAC Flooding
#### ICMP PING

- internet control message protocol
- protocol number 1 (in IP)
- Does not convey data
- Used to check whether computers are live and up

#### Traceroute

- identify the path from you to the server
- shows where the path fails

#### Transmission Control Protocol

- establishes sessions to control packets arrival to their destination
- includes the concept of a port which can be in one of three states
	- open
	- closed
	- filtered

TCP Scan - positive service discovery / negative service discovery / no inference
/ TCP SYN Scan / TCP FIN Scan / TCP XMAS Scan / TCP ACK Scan /

![[Pasted image 20250123123005.png]]

![[Pasted image 20250123123109.png]]

![[Pasted image 20250123123226.png]]

![[Pasted image 20250123123309.png]]




