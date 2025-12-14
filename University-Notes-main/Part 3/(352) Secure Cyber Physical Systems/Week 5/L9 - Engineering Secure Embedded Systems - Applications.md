
## Reality

- developing secure resource constrained CPS applications is hard, resources are limited (ram and rom)
- security techniques - an overhead some arent willing to pay

## Agenda

1. Memory Allocation
2. Securing Sensitive Information (in transit)
3. Securing Sensitive information (At rest)

- wasted space due to padding : information on slides


Memory Fragmentation - External

- memory has been allocated in contiguous blocks for M1 and M2
- there is enough free space for M3
- Except this free space is not contiguous 
![[Pasted image 20251105095132.png]]
- So cannot allocate M3


alternatives to heap-based allocation


heap based can be useful, but we might have an uncertain number of items that need storing in memory

Solution - stack allocation
- be really careful
Solution - memory pools


a statistical sized array of items of fixed sizes 
	need to define at compile time how many items can be in the pool
never going to be fragmentation as items are all the same size
- caveat this is within the pool, might be fragmentation between pools

note on coroutines

 You have been using async / await in
Python for the labs
• Expressing IO operations using coroutines
typically nicer than other approaches (e.g.,
callback / polling)
• Problem: C++ coroutines (as part of the
C++20 standard) requires dynamic memory
allocation
• Some alternate C++ libraries may help
avoid memory allocation [2]
• Other languages such as Rust avoid needing
dynamic memory allocation by using
stackless coroutines


coroutines involve cooperative scheduling
- a new coroutine cannot be scheduled until the current one yields its excecution
- this opens the potential for denial of service attacks if coroutine does not yield often enough
- there will often be a hardware counter (the watchdog timer) that resets the CPU if the watchdog is not polled often enough by the scheduler


### securing sensitive information (in transit)

#### TLS - Transport Layer Security

- offers confidentiality and integrity for transmitted packs
	- typically a shared secret is generated using ephemeral Diffie-Helman key exchange which is used to encrypt packets
	- Ephemeral means that a temporary key is generated for each connected (to provide forward secrecy)
	- can these constrained devices generate keys frequently?
	- do they have space to store the keys?
- TLS tends to be a fairly heavyweight protocol

#### DTLS - Datagram Transport Layer Security
- using tcp might be expensive for some CPS
- like tls but instead built on top of UDP
- UPD is unreliable, DTLS uses simple retransmissions to handle
- packets designed to be small enough to avoid being fragmented
- networks have a maximum transmission unit - maximum size of a packet
- 1500 bytes for ethernet 
- 127 fo IEEE 802.15.4

TLS vs DTLS
- provides confidentiality
	- integrity
	- non-repudiation
	- authenticity checks
- replay detection is optional and may be disabled with DTLS

#### OSCORE

a security layer specific to CoAP
provides confidentiality and integrity protection
intended to not protect all information in CoAP headers
when routing through a proxy this information can change


#### OSCORE vs DTLS

- CoAP over DTLS is slightly more expensive than OSCORE in terms of 
	- latency 
	- ROM usage
	- CPU usage
	- Network
	- Energy

#### Wireshark - OSCORE

Only supports processing unencrypted packets and AES_CCM_16_64_128

Does not support other cipher suites

not support for upcoming group oscore standard


#### Securing Sensitive Information (At Rest)

- a reminder:
	- we have discussed: Firmware encryption, Mitigating against firmware extraction attacks, using trusted firmware-M APIs to store secrets in secure enclaves of a CPU
- What is the application going to do differently to protect sensitive information at rest?

