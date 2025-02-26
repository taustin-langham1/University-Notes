
**[Week 3 lecture slides](https://modules.lancaster.ac.uk/mod/resource/view.php?id=2596809)**
- basic security services of cryptographic systems
- introduce cryptosystems and the security services they offer
	- Encryption systems
	- Signature schemes
- Hash functions 

define security services and name cryptographic systems that can provide them
describe the basic operation of an encryption scheme and a signature scheme
understand the potential attacks against these generic systems and understand what level of security is usually required in practice
define a cryptographic hash function and the properties of hash functions

### What is cryptography

- the art of writing or solving codes
- typically used to obscure or verify data

1. it defines what it means to be secure in a precise mathematical way
2. it involves designing systems to achieve these precise definitions
3. and proving that they do so


- cryptography does not concern itself with availability
- it cares about confidentiality and integrity

#### Security Services

- Security services are the specific security goals that we may want to achieve
	- confidentiality
	{- data integrity 
	- data origin authentication
	- non-repudiation } - (all three of these are sort of mainly concerned with integrity of data)



#### Defining Security: Attacker Capabilities

- kerckhoff's principle: A cryptographic system should be secure even if everything about the system, except for the key, is public knowledge

- attacks can be categorized as passive or active attacks

- passive attacks - no processes change to data or processes
	- unauthorised access to data
	- traffic analysis 

- Active attacks - usually involve change to the data or to a process carried out on the data
	- masquerade
	- replay attack
	- modification attack
	
#### Types of Cryptosystems
- encryption systems
- systems for data integrity 
	- message authentication codes (MACs)
	- digital signatures
- Hash functions

An encryption system: Notations

![[Pasted image 20250129112016.png]]




##### Security of an Encryption System


- we aim to provide confidentiality of plaintext messages
- What do we assume the attacker knows?
	- The encryption/decryption algorithm
	- the encryption key
	- all ciphertexts
- Goal: Discover the decryption key
	- exhaustive key search
	- usually used as a benchmark for security
- Goal: Recover a plaintext message from a ciphertext

##### Plaintext message recovery

- Ciphertext-only attack 
	- Passive attacker that knows only ciphertexts
- Known-plaintext attack
	- active attacker knows some plaintext and ciphertext pairs
- Chosen-plaintext attack

	•Active attacker that knows plaintexts and ciphertext pairs, where the plaintext is chosen by the attacker.

	•Modern encryption systems are usually designed to withstand (at least) this attack.

•Chosen-ciphertext attack

- Active attacker that knows plaintext and ciphertext pairs, where the plaintext and ciphertexts can be chosen by the attacker

### Digital Signatures


- are an asymmetrical crypto system - (not mac cryptosystem)


#### Security of a Signature Scheme

- we aim to provide data integrity, data origin authentication and non-repudiation

- what do we assume the attacker knows?
	- The signing/verification algorithm 
	- the verification key
	- all message/signature pairs
- Goal: Create a forgery
	- Selective forgery: attacker outputs a signature for a specific message
	- Existential unforgeability: attacker outputs a signature for a messages chosen by the attacker


### Hash functions

-  a cryptographic hash function must:
	- Be a compression function
	![[Pasted image 20250129113932.png]]
	- Be easy to compute 


- ![[Pasted image 20250129113941.png]]


#### Security of hash functions

- a cryptographic hash function should provide the following properties
	- Preimage resistance: given a hash y, it should be computationally difficult to find a message m such that h(m) = y
	- second preimage resistance: given a message m and a hash h(m), it should be computationally difficult to find a message m' such that m =/= m' and h(m) = h(m')
	- Collision resistance: it should be difficult to find two messages m and m' such that m =/= m' and h(m) = h(m)


#### Collision resistance

- hash functions always have collisions
- but these collisions should be difficult to find
- so how long should the output of a hash function be to make finding collisions difficult?

 •This is related to a problem in probability theory called the birthday problem.

•Birthday attacks  are often used to find collisions in hash functions: how many messages do we need to randomly select before there is a greater than 50% chance of a collision?

•It turns out, this is equal to the square root the number of possible hashes: 2^(n/2) where n is the bit length of the hash function.

![[Pasted image 20250129114707.png]]
