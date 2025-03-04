**[Week 7 Slides](file:///home/thomas/Downloads/Week%2017%20-%20Wireshark.pdf)**



- Learning objectives 

 - wireshark interface
 - capture filters and display filters
 - interrogation through statistics
 - application layer filtering
 - Conversation tracing 

- What is Wireshark?
	- Network reconnaissance 
	- Vulnerability identification
	- identification of attack vectors

# Wireshark

Ethics 

- using wireshark to examine packets without permission is illegal
- Balancing privacy and security is fundamental ethical dilemma 
- privacy invasion, psychological damage and harm to reputation
- wireshark is a passive sniffer, and therefore hard to detect
- a network protocol analyser or spyware
- non-maleficent obligation

![[Pasted image 20250227121930.png]]



OSI better for academic, TCP model for industry troubleshooting


![[Pasted image 20250227122221.png]]

ICMP -> internet control message protocol

ARP -> Address resolution protocol -> mac address relating to an ip address


Wireshark filters:

- conversation filters
- lower-level filters
- statistical filters
- range operations
- combination filters
- application level filtering 


#### Conversations

- choose an IP in source or destination and apply as filter
- Choose another column apply as filter and selected
- Choose protocol and filter to that
- this will isolate to conversation recipients only