

##### authorization and accountability
###### Access control procedures

###### Mandatory access control and discretionary access control

###### Administration of privileges and access monitoring


### Access Control (1)


A collection of mechanisms that work together to create security architecture to protect the assets of an information system

one main goal of access control is *personal accountability*
which is the mechanism that proves someone performed a computer activity at a specific point in time

### (2)

who is allowed to do what?
who, a person machine an app
what, an action on an object
action, read write execute
object, a file directory data service

determines who is allowed to access certain data, apps, and resources - and in what circumstances

security policy, expresses who is allowed to do what

### Authorization

checks whether an access request for an object originating from a principal should be granted or denied

- the reference monitor is the guard enforcing the policy
- the policy is given in an access control list
- the ACL is attached to the object
- setting the policy also called authorization
- finding the rules applicable for a given access request


### Accountability

security goal that generates the requirement for actions of an entity to be traced uniquely to that entity. This supports nonrepudiation, deterrence, fault isolation, intrusion detection and prevention, and after-action recovery and legal aciton

supports processes that are launched after events had occurred

- Regular audit that checks whether an organization compiles with the existing regulations
- Technical audit that scans logs in search for signs of a cyber attack
- investigation triggered by an incident that tries to identify the vulnerabilities exploited
- investigation that tries to identify the parties responsible 


### information owner

- an information owner is one who maintains overall responsibility for the information within an information system
- the information owner must be the one to make the decisions about who uses the system and how to recover the system in the event of a disaster

Access control -> physical and logical

#### Physical access control

- use of locks, security guards, badges and similar admin measures
- control the ability of people or vehicles to enter a protected area by means of authentication and authorization
- prevent an attacker from gaining physical access to the system

#### Logical access control

- the use of procedures relating to information and knowledge
- require the validation of an individuals identity through some mechanisms, such as PIN, card, biometric, or other token
- prevent an attacker from exploiting logical access gained to the system


### Primary security concerns

CIA triad

loss of confidentiality
loss of data integrity 
loss of data availability


### Access control procedures 

- allocation of privileges
	- limitation on the type of access

- Administration of privileges
	- recording of privileges
- Monitoring accesses
- prevention of unauthorized access
- identification and authentication of users

### Allocation of privileges

![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 2/images/Pasted image 20250122111843.png]]


### Mandatory access control (1)

The security policy is centrally controlled by a policy administrator and is guaranteed (in principle) to be enforced for all users

the system decides who gains access to information based on the concepts of subjects, objects, and labels

subjects - the people / other systems that are granted a clearance to access an object within this system
objects - the elements within the information system that are being protected from use or access
labels - the mechanism that binds objects to subjects. a subjects clearance permits access to an object based on the labeled security protection assigned to that object

### (2)

- all users have a security clearance 
- all files have a security classification
- set of rules for users access to files

![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 2/images/Pasted image 20250122112308.png]]


### Discretionary access control

- the principle of DAC dictates that the information owner grants privileges to users to access the system
- it is a decentralized access control policy that allows subject to control access to objects
- most of the common operating systems on the market today rely on DAC principles for access and operations


### Access control lists

-  a list / file of users who are given the privilege of access to a system or resource
- consist of a user ID and an associated set of privileges for that user and that resource
- the privileges are typically read, write, update, execute, delete, or rename

### the least privilege (need-to-know)

- the principle of least privilege is the predominant strategy to assure confidentiality
- the objective is to give people the least amount of access to a system that is needed to perform the job they are doing
- the need-to-know dictates the privilege to perform a transaction or access a resource

### Role-based access control (RBAC)

- role based control simplify the job of granting and revoking access by simply assigning users to a group, and then assigning rights tot he group for access control purposes
- rbac methods are most appropriate where there is high turnover of employees, and/or frequent movements between job roles
- separation-of-duties policies stop single users from becoming too powerful

### Administration of privileges

- hand over the privileges
- informing the user of responsibilities associated with the privileges
	- limits, consequences, actions which may need to be taken, reporting procedures
- recording of the privileges
	- can you readily identify the users with privileges 
- revocation of the privileges
	- can this be done without the cooperation of the user
	- who needs to be informed

### Handing over the privileges

- identity of recipient
- security of handover phase

### Digital rights management (DRM)


DRM imposes the security policy of an external party on the system owner rather than protecting the system owner from external parties

DRM needs tamper resistant roots of trust

- roots of trust, level of tamper resistance required depends on threat model


### monitoring access
- is a defense against access control loopholes
- provides evidence of a security incident 
- provides a model for normal behavior


### why monitor a system?

- collect evidence for security incidents 
- collect data to model normal behavior
- legitimate users become tempted to nullify access control safeguards

Active monitoring of password systems provides:

- feedback to users of previous successful and unsuccessful logins
- evidence of password experimentation
- evidence of logins when the user is know to be absent

### level of logging

logging at high level may fail to reveal attacks due to software or implementation flaws

logging at low level will present major impact on performance, massive volume of audit data and insurmountable analysts problems


### event logs

- accountability makes use of event logs, kept by OS, by networking devices, or by applications
- Audit policies define which events will be logged
- attackers may hide their traces by deleting incriminating log entries once they have acquired sufficient privileges but should not be able to tamper with the evidence already logged
- tamper resistance of a log could rely on physical measures like writing the log to WORM (write-once read-many) memory or on cryptography (hash chain)
- privacy rules can have an impact on the events that may be logged; logging trials may have unintended privacy impacts

### storage security levels

![[Part 2/Secure Cyber Systems/In_Lecture_Notes/Week 2/images/Pasted image 20250122114311.png]]

### hashing

instead of user password, store hash of password
when user enters password, compute its hash and compare with entry in password file
- system does not store actual passwords!
hash function H must have some properties
- one-way given H(password), hard to find password
	- no known algorithm better than trial and error
collision-resistant given H(passsword1), hard to find password2 such that
H(password1)=H(password2)
- it should even be hard to find any pair (p1,p2 s.t. H(p1)=H(p2))

salting, brute force attack, rainbow table attack, dictionary attacks
