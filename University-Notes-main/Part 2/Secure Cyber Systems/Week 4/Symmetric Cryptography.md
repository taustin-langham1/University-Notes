


**[Week 4 Slides](file:///C:/Users/langh/Downloads/lecture4-symmetriccrypto.pdf)**

- Symmetric encryption schemes 
	- stream ciphers
	- block ciphers
- Message Authentication Codes

Describe basic operation of stream and block ciphers

Understand the features of different modes of operation for bock ciphers, and pick and appropriate mode  of operation for an implementation
describe advanced encryption (AES) and its features
Describe the basic operation of a message authentication code
(MAC) and understand the security services it provides


## Types of Symmetric Encryption systems

### Stream cipher
![[Part 2/Secure Cyber Systems/Week 4/Images/Pasted image 20250205110706.png]]


- take as input a (short) key
	- key is often combined with an initialization vector (V)
- Key is converted into a continuous keystream
- working with one bit at a time, and the plaintext is mixed with the keystream
- Advantages of stream ciphers
	- No error propagation
	- on-the-fly-encryption => good choice for real-time services 
	- fast and easy to implement, especially in hardware
- Require sender and receiver synchronicity

- e.g., A5/1, RC4


### Block cipher

![[Part 2/Secure Cyber Systems/Week 4/Images/Pasted image 20250205110713.png]]

- take as input a key and a block of plaintext and outputs a block of ciphertext
- a good block cipher should be designed to provide confusion and diffusion
	- confusion hides the relationship between the plaintext and ciphertext
	- diffusion spreads the statistics of the plaintext
- Usually obtain protection from chosen plaintext attacks if the block cipher behaves like a pseudorandom permutation
- Block length should be chosen to ensure a balance of efficiency and security


E.g., 
- DES - data encryption standard
- AES - Advanced encryption standard
- IDEA - international data encryption algorithm
- Camellia


### Advanced Encryption Standard

- Round function
	- operated on 16 bytes of input
	- substitution-permutation network
- A round key ki is derived from the secret key k
- to decrypt, encryption steps are performed in the reverse order
- AES supports key sizes of 128, 192, and 256
- AES is very fast

![[Part 2/Secure Cyber Systems/Week 4/Images/Pasted image 20250205112712.png]]



### Modes of operation


###### Electronic code book (ECB)

- no processing
- simply just runs encryption algorithms
- little error propagation
- deletion and insertion block attacks (vulnerable to)

###### Counter Block chaining (CBC)

- little processing
- then encrypt result
- then that cipher key will be xor'd using the previous cipher text

- much more secure to insertion and deletion attacks than ECB
###### Cipher Feedback (CFB)

- similar to CBC but the first ciphertext is just used to encrypt the next key
- taking block cipher and turning into a stream cipher 
###### Counter (CTR)

- encrypt a counter
- update counter and continue updating counter at each encryption round

- widely known and commonly used 

![[Part 2/Secure Cyber Systems/Week 4/Images/Pasted image 20250205113842.png]]
### Padding

- many block ciphers **require** the message to be a multiple of the block size
- **Padding** extends a plaintext message to a multiple of the block size
- E.g., Bit padding, Zero padding, PKCS7

### Block Ciphers: Advantages and Disadvantages


Advantages

- Versatility
- Adaptability
- Compatibility


Disadvantages
- Error propagation
- Need for padding
- Speed in hardware

## Message Authentication Codes

![[Part 2/Secure Cyber Systems/Week 4/Images/Pasted image 20250205114414.png]]




### Examples:


#### HMAC
- can be constructed from any hash function
- let h be a hash function and k1 and k2 be two symmetric keys
- compute a MAC for a message m in two steps 
	- tag = H(k1 || H(k2 || m))
- to verify, repeat the two above steps and check the output is identical
#### CBC-MAC
- CBC-MAC uses counter block chaining mode of operation
- it can be constructed using any block cipher
 • Let 𝐸 be a block cipher, 𝐼𝑉 be an initialization vector
and 𝑘 be a symmetric key.
• Compute a MAC for a message 𝑚 = 𝑚1𝑚2 … 𝑚𝑁 as
• 𝑡𝑎𝑔 = 𝑐𝑛
• To verify, repeat the above two steps and check the
output is identical


### MAC's and Security Services

• MACs provide data integrity and data origin authentication:

• Secrecy of the symmetric key means the MAC cannot be changed if data
changes, so changes to the data are detectable.

• It is unlikely that a different key will work to construct a MAC, which means
that we have some guarantee of who constructed the MAC.

• MACs do not provide non-repudiation.

• MACs can be combined with encryption scheme to provide
confidentiality and data origin authentication.

• Encrypt-then-MAC provides protection against chosen ciphertext attacks.

• Requires encrypting the plaintext, and then computing a MAC for the ciphertext