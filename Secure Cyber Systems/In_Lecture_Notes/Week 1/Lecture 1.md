# 252
###### Induction and Lecture 1 Content (Authentication)

# Induction and Introduction

module aims: 
	- Authentication, Authorization and Accountability (AAA)
	- fundamentals of cryptosystems and apply them in a lab environment 
	- relate security fundamentals with operating systems and network security
	- employ formal methods for assessing the cyber security of systems

## Module Content 

![[Pasted image 20250115140526.png]]

# Authentication

Access controller?


##### Learning Objectives
#### understand concept of authentication
#### know the typical authentication factors
#### understand the advantages and limitations of each authentication method
#### know the concept of multifactor authentication

## What is authentication?

#### authentication concept

- authentication verifies an entities claimed identity
- the identity must make sense to the verifier 
- local identifier (for specific established environment)
- global identifies (for identification outside of environment, justification)

###### Authentication of users

- must prove that they are the persons corresponding to the claimed identity
- system must be assured that attackers cannot masquerade as legitimate users
- users must be assured that the system (and others) cannot subsequently masquerade as the user and that they're communication with legitimate systems. 

###### Authentication Factors

- three main authentication factors
	- something the user knows
	- something the user has
	- something the user is

![[Pasted image 20250115141119.png]]


#### I) something the user knows

- knowledge-based Authentication
	- password
	- PIN
	- Pass phrase
	- personal data
	- word association
##### Graphical password

- users have to interact with images than texts

##### Password / PIN Advantages, Disadvantages and Alternatives

Knowledge-based Authentication
###### Advantages
	- Cheap
	- easily revoked
	- user acceptance
	- high security potential

###### Disadvantages

- user accountability
- no control on privilege once handed to user
- user may be unaware of compromise 
- demands upon user
- eavesdropping and illicit capture
- can be captured by masquerading system
- password leak to untrustworthy host

###### Alternatives

one-time passwords

- the user proves secret knowledge or access to secret knowledge 
- the user's responses are different on each occasion
- eavesdropped or captures passwords cannot be reused
- most techniques demand access to some device, and are discussed under "something the user has"


##### Textual Password Cracking 

###### Two approaches to password cracking 

- brute force (attempt all possible combinations)
- Dictionary attacks (check popular/likely passwords)

###### Password cracking 

- determine which has function has been used and possible salt
- decide which attempt to use
- dictionary attacks are often sufficient for "any account" cracking 
- brute force may be required for "particular account" cracking
- locate/acquire necessary resources for password cracking 

###### Graphical password cracking

issues: 
	- brute force attack (many possible patterns)
	- pattern bias (start and end points)
	- smudge attack (oily residue)

#### ii) something the user has

magnetic stripe card
one-shot password token
	- synchronized password generations
	- challenge-response
Smart cards
- stored data card, secure storage of data such that its contents can be neither copied nor modified in an unauthorized manner
- card with processing capabilities - has an imbedded microprocessor in addition to data storage capabilities

###### Magnetic stripe card

- used widely in banking systems
- identification information includes special printing/holograms
- written signature and customer data recorded on magnetic stripe
- major disadvantage is that it is easy to counterfeit 

- cheap and universally accepted
- though its security and functionality is limited 

##### One-shot password token

- synchronized password generators 
	- produce the same sequence of random passwords in a token and at the host system
		- clock on token
		- sequence generator token
- Challenge-response 

Synchronized password: clock on token
![[Pasted image 20250115141151.png]]


- correct display is given if correct pin is keyed
- system clock is included in algorithm calculation to ensure freshness and one time property 
- users key in token output at terminal
- fails if there is a loss of synchronization between clocks


###### Challenge response system
![[Pasted image 20250115141204.png]]
- a family of protocols in which one party presents a question and a party must provide a valid answer
- user and system share a secret key

###### Summary of challenge response system process

 user logs into the host system entering the userID
• host generates a random number (the challenge) and displays it at the terminal
• user enters a PIN into the token keypad, followed by the challenge
• response is computed as a cryptographic one-way function of the challenge, in-built
key and PIN, and read off the token LCD display
• user keys this response into the terminal
• host system performs a similar computation using the PIN and key values stored with
the userID
• login proceeds if the results of the host computation check out against the response
entered by the user

Advantages

- Attacker must obtain a token
- users cannot share token
- token combines with other methods
- users aware if token lost
- illegal token possession is evidence


###### Disadvantages

- Cost
	- of token
	- of reader or checking mechanism
- Administration
	- distribution
	- recording
	- lost token reporting
	- replacement of expired tokens
	- destruction



#### iii) something the user is 

Biometrics: automated methods of verifying or recognizing a person based upon a physical or behavioral characteristic

basic processes: 
	- analog capture of the users attribute
	- development of a template of the users attribute
	- comparison of the input template with that of a stored value when access is requested
	- decision on access acceptance or rejection

###### Biometric classification

- physiological behaviors and approaches
	- use measurements from the human body such as fingerprint, face, iris, retina, ect...
	- use measurements from human action such as voice, signature, keystroke, touch, ect...

###### Biometrics systems

• Fingerprint recognition
• Eye retina scanning
• Iris scanning
• Palm print
• Written signature dynamics
• Voice print
• Keystroke dynamics
• Touch dynamics
• Face recognition
• Brainwave
![[Pasted image 20250115141225.png]]



##### multifactor authentication

with 2 or 3 factors to authenticate, an information owner can have confidence that users who access their systems are indeed authorized

TFA
- The user has a physical device (like a card) that contains their credentials, protected by a personal identification number