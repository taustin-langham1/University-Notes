**[Week 5 Slides](file:///C:/Users/langh/Downloads/lecture5asymmetriccrypto.pdf)**
#### Lecture Outline

- Diffie-Hellman key exchange 
- Public Key Encryption 
	- RSA
- Digital Signatures
	- RSA signatures

- Diffie-Hellman key exchange to generate a shared secret
- explain how RSA encryption and decryption operates
-  Explain how to implement RSA encryption securely
- Describe how to modify RSA into signature scheme and understand the security services it provides


#### ASYMMETTRIC (public-key) cryptography
- provides a mechanism to construct a shared secret
- asymmetric keys means no need to share a secret

## Diffie-Hellman Key Exchange

- used to securely exchange a key
- Requires two system-wide parameters
	- a prime number `p`
	- a special number `g` (a generator)


why is it secure? 
- discrete logarithm problem is hard. (i.e., for known elements `a, b and p,` find an element `x` such that `a^x = b mod p`


- EI Gamal
	- security depends on hardness of the discrete logarithm problem
- RSA 
	- related to the hardness of integer factorization
		- given an integer `N = p X q`, find `p and q`, where `p and q` are primes
- Rabin
	- related to the hardness of integer factorization


RSA

- one of the most widely used public-key cryptosystems in use today
	- key gen
	- encryption
	- decryption
	- security of RSA


### generating an RSA keypair

create the public key `pk`

1. choose two large prime numbers `p` and `q`.
2. let `n = p x q`.
3. Choose an element `e` that is coprime to `(p - 1)(q - 1)`.


the public key is `pk = (n,e)`.

- generate the secret key `sk:`
	- let `d` be a modular inverse of `e` such that `e x d = 1 mod (p - 1)(q - 1)`
	
- the private key is `sk = d`

#### In practice:

![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 5/Images/Pasted image 20250212112114.png]]

### RSA Encryption and Decryption


- to encrypt a message `m` using public key `pk = (n,e):`
	- `c = m^e mod n`
- to decrypt a ciphertext `c` using secret key `sk = d:`
	- `m = c^d mod n`

#### In practice:

![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 5/Images/Pasted image 20250212112815.png]]


### Security of RSA

- several ways to attempt to break RSA:
	- Recover the decryption key from the encryption key
		- if the modulus `N` is chosen large enough recovery of the decryption key is hard
	- Decrypt the ciphertext without the secret decryption key
		- this is equivalent to braking the RSA problem, another mathematically hard problem

- RSA is a deterministic algorithm
- a Padding scheme must be used to achieve a probabilistic encryption system


### RSA-OAEP

- Let `h1` and `h2` be two hash functions and let `r` be randomness generated using a random number generator
	- to encrypt a message `m` using public key `pk = (n,e):`
			![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 5/Images/Pasted image 20250212113350.png]]
	- to decrypt a ciphertext c using secret key `sk = d:`
			![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 5/Images/Pasted image 20250212113423.png]]


### Strengths and Weaknesses of Public-Key Encryption

- Strengths:
	- Does not require secure key exchange
	- No need for symmetric trust
- Weaknesses
	- Slow encryption speeds
	- security issues when encrypting long plaintexts


## Digital Signature Schemes


message -> signing algorithm (with signing key`sk`) -> m,o = sign sk (m) -> verification algorithm (with verification key `vk`)-> verification bit

### Example: RSA Signatures
![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 5/Images/Pasted image 20250212114036.png]]
### Example: Security of Digital Signatures

- digital signatures should provide:
	- data integrity
	- data origin authentication
	- non-repudiation

- digital signatures can be combined with encryption to provide confidentiality in addition to the services above
## The Future of Publix Key Cryptography

### Towards Post-Quantum Public Key Cryptography

- PROBLEM: If an attacker can access a quantum computer, none of the problems upon which public-key cryptography is based will be hard
- Shor's algorithm can factor a number `O(b^3)` where `b` is the number of bits
- we need post-quantum cryptography that is based on problems that are believed to be hard even with access to a quantum computer!
	- NIST standardization efforts

