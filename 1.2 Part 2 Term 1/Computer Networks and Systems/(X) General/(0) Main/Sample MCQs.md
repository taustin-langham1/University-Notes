

# 1 

1. Which type of addresses are used for communication within a
sub-network and for host-to-host packet delivery on different
networks, respectively? [1 Mark]
• A. DNS addresses and MAC addresses
• B. Port numbers and IP addresses
• C. MAC addresses and IP addresses
• D. IP addresses and DNS addresses


within the same subnet for host-to-host

Source/Destination IP: Hosts use private ips

MAC addresses: hosts resolve IPS to MACs via ARP

other networks and the addresses they use

a) local networks
	- private IPs, Ethernet frames to have direct communication between hosts

b) remote network, for different subnet 
- routing, via gateway
- NAT translates private -> public IP


# 2

2. Which of the following is NOT the essential part of the TCP? [1
Mark]
• A) Segmenting data into smaller units
• B) Ensuring end-to-end delivery of data
• C) Providing encryption for data security
• D) Handling flow control and error detection

NOT essential:
C


# 3

• 2. Choose the correct statement(s) [2 Marks]
• A) In P2P file sharing application, packets may follow the different
routes _/
• B) P2P application and Device to Device communication are same
concepts
• C) For P2P application the user devices need to be in the same location
• D) In a P2P application, each device acts as both a client and server _/_




# 4

4. Let R: link bandwidth (bps), L: packet length (bits) and a: average
packet arrival per second. The packet loss due to buffer overflow
event will happen if [2 Marks]
• A) La/R ~ 0
• B) 0< La/R <1
• C) La/R >1 _/
• D) La/R =2



# 5

4. Choose correct Statements. [3 Marks]
• A) We can turn our window/linex OS PC to act as a router.
• B) Routers do have system software
• C) Network-core devices do not run user applications
• D) Routers firmware is an example of system software

all!



# 6

4. What does the DNS command nslookup -type=ns
lancaster.ac.uk do? [2 Marks]
• A) Tells that all the mails sent to “@lancaster.ac.uk” should
be routed to the Mail server in that domain.
• B) It will output the name servers which are associated with
the given domain.
• C) It will return the time zone information.
• D) Sends an HTTP request at port 80

B


DNS:
	translates human readable domain names into machine readable IP addresses
	- When you visit a website, your device queries a DNS server to resolve the domain to an IP.
####  **DHCP (Dynamic Host Configuration Protocol)**

- automatically assigns IP addresses and network configuration (subnet mask, gateway, DNS) to devices on a network

DHCP Request - device broadcasts DHCP server
DHCP offer - the server responds with an available IP
DHCP Request again - the device accepts or whatever
DHCP ack - the server confirms, and leases the IP

just eliminates manual IP config


# 7

5. Select correct statements [2 Marks]
• A) In Go Back N receiver always send ACK for correctly-
received packet so far, with highest in-order seq #
• B) In Go Back N if sender receive a duplicate Ack, it
retransmit all already sent packets
• C) In Go Back N sender ignores the duplicate Acks
• D) In Go Back N upon a timeout event, the sender retransmit
all already sent packets
• E) None of above

• 8. In TCP the size of flow control window is determined
based on network congestion [1 Mark]
• A) Yes
• B) No