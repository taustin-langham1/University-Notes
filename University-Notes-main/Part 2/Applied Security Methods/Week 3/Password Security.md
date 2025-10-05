**[Week 3 Lecture Slides](https://modules.lancaster.ac.uk/pluginfile.php/3929559/course/section/462271/3%20Passwords.pdf)**
#### What is a password

- A shared secret used to gain access to a system
	- known to: 
		- A user of the system
		- the system itself

- three classes of secrets:
	- Something you know
		- a password
	- Something you have 
		- smart card or smart phone
	- Something you are
		- Fingerprint, voice scan, iris


##### Why is obtaining a password important?

- intial access
- privilege escalation
- lateral movement



##### How to measure uncertainty with Entropy

- entropy is a measure of uncertainty
- minimum uncertainty when:
	- You know an event will never happen
	- You know an event will definitely happen
- Maximum uncertainty when:
	- Probability of events is the same


###### Entropy with multiple events


![[Pasted image 20250130120602.png]]


- why is high entropy desirable?
	- We want strong passwords that take a long time to guess
	- n bits of entropy means 2n combinations for the adversary to search
	- A higher entropy implies a greater number of combinations of symbols that need to be checked which increases the time to crack a password

- How does high entropy translate into strong password security
	- More combinations => more checks required => longer time for adversary to crack password
	- so the implication is the higher the entropy of the password, the greater its strength
	- ![[Pasted image 20250130120858.png]]


#### limitations of using entropy

	- Humans will not generate a password where the probability of choosing each symbol is uniform
	- different languages will use some symbols more than others
	- the probability of a symbol occurring will depend on the previous symbols


- consider what is the alphabet used to construct the passwords
- passwords may have a relatively high entropy but will not always be strong



### Password Management

- checking passwords
	- the system must validate passwords provided by users
	- thus, passwords must be stored somewhere
	- basic storage: plain text



#### Problem: Password File Theft

-  Attackers often compromise systems
	- They may be able to steal the password file
	- Linux: /ect/shadow
	- windows: C:\windows\system32\config\sam
- If the passwords are plain text, what happens?
	- The attacker can now log-in as any user, including root/administrator
- Passwords should never be stored in plaintext


##### Hashed Passwords

- key idea: store hashed passwords, not plaintext ones
- used one-way cryptographic hash functions
	- sha256,sha512,sha3,shake
- easy to go from input hash, hard to find input from hash
- never encrypt passwords!


- cryptographic hash function transform input data into scrambled output data
- deterministic: hash(s) always returns the same hash result for the same input s
	- high entropy
	- collision resistant
	- locating s' such that hash(s) = hash(s') takes a long time


#### Strategies for cracking passwords

##### Attacking password hashes

- cryptographic hashes are collision resistant
- so target weak poor passwords
- weak passwords enable dictionary attacks


- common for 60-70% of hashed passwords to be cracked in <24 hours


##### Hardening Password Hashes

Key problem: cryptographic hashes are deterministic

• hash(‘p4ssw0rd’) = hash(‘p4ssw0rd’)
• This enables attackers to build lists of hashes
• Solution: make each password hash unique

• Add a salt to each password before hashing
• hash(salt + password) = password hash
• Each user has a unique, random salt
• Salts can be stored in plain text


- stored passwords should always be salted
	- forces the attacker to brute-force each password individually
- Problem: it is now possible to compute cryptographic hashes very quickly
- GPU computing: hundreds of small CPU cores
- NVIDIA GeForce GTX Titan Z: 5,760 cores
- GPUs can be rented from the cloud very cheaply
- 2x gpus for 0.65 per hour

#### Examples of Hashing Speed

- a modern x86 server can hash all possible 6 character long passwords in 3.5 hours
- upper and lowercase letters, numbers, symbols
- a modern gpu can do the same thing in 16 minutes
- most users use dictionary words, no symbols
- predictability makes cracking much faster

#### Hardening salted passwords

- Typical hashing algorithms are too fast
	- Enables GPU's to brute-force passwords
- Solution: use hash functions that are designed to be slow
- e.g., bcrypt,scrypt,PBKDF2
- these algorithms include a work factor that increases the time complexity of the calculation
- scrypt also requires a large amount of memory to compute, further complicating brute-force attacks


1. Never store passwords in plain text
2. Always salt and hash passwords before storing them
3. Use hash functions with a high work factor




• Problem: hashed passwords cannot be
recovered

• This is why systems typically implement
password reset

• Use out-of-band info to authenticate the
user

• Overwrite hash(old_pw) with
hash(new_pw)

• Do not implement a system that can send a
user their password


