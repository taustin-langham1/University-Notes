## **what are the two types of reconnaissance? and explain their differences**

**passive reconnaissance - gathering information on target**

**active reconnaissance - gathering information on target where potential exists where your actions will be seen by the target / actively changing data without targets consent** 

## **define OPEN SOURCE INTELLIGENCE and give its scope**

OSINT is intelligence produced from publicly available information and is collected, exploited, and disseminated in a timely manner to appropriate audience for the purpose of addressing a specific intelligence requirement 


## Network sniffing


### Passive
1. What is passive network sniffing
	1. monitoring network, without injecting any data, making it difficult to detect
2. What is sniffing?
	1.  capturing network traffic
3. What is a sniffer?
	1.  software that captures packets off network
4. **What is SPAN/mirror port**
	1.  **on a switch, send a copy of all traffic out this port to sniffer**
5. **What is TAP**
	1.  **hardware device, taps a network cab**
6. What is packet capture
	1.  act of capturing the entire packet or packet headers for analysis
7. What is promiscuous mode
	1.  network card mode host listens to all traffic on the network, not just what is address or destined only to itself
8.  how does a packet sniffer work?
	1.  HTTP, FTP, **SNMP, SMTP**
9. What's the difference between Shared Ethernet vs Switched Ethernet
	**Shared** 
	1. all systems connected to the same bus and in the same broadcast domain
	**Switched**
	2. machines connected to a switch, not a shared bus, the switch maintains the MAC table, and keeps track of each computer MAC address and the physical port it is connected to

### Active
1. **What is active reconnaissance?**
	1. What is active network sniffing 
		1.  Packets captured in a switch infrastructure or where the attacker is
			actively sending network traffic
	2. what is ICMP Ping
		1. Used to check whether
			computers are live and
			up
	3. What is traceroute
		1. Identify the path
			from you to the server
			& Shows where the path fails
	4. What is the TRANSMISSION CONTROL PROTOCOL
		1.  Establishes sessions to control
			packets arrival to their
			destination

			includes the concept of a port
			which can be one of three state: OPEN CLOSED FILTERED

	5. What is TCP scan: positive SD, Negative SD, No inference, SYN, FIN, XMAS, ACK
		1.  SYN -> 
		 <- SYN/ACK 
		 -> ACK
		"yay service"
		
		2. SYN -> 
		   <- RST 
		"hmm okay no service :("

		3.  SYN -> "port is filtered"
			SYN -> "port is filtered"
			SYN -> "port is filtered"
			
		"connection has timed out :("


		4.   SYN -> 
		 <- SYN/ACK 
			"TERMINATE CONNECTION >:)"
		 -> RST
		