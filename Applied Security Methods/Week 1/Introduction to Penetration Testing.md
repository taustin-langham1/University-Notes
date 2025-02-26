## What is Penetration Testing?

- finding and exploiting vulnerabilities in a computer system
- a simulated attack, to identify weak spots
- can be automated with applications or performed manually

#### types of penetration tests

> zero knowledge
> 	- Testing as Attacker (black box testing)

> full knowledge 
> 	- Testing as Developer (white box testing)

> Some knowledge
> 	- Testing as a user with access to some data (gray box testing)


Hacking vs Penetration testing

![[Pasted image 20250116120606.png]]


#### Computer misuse act

- unauthorized access to computer material
- unauthorized access with intent to commit or facilitate commission of further offences 
- unauthorized acts with intent to impair, or with recklessness as to impairing, operation of computer
- unauthorized acts causing or creating risk of, serious damage

#### Bug bounties

- rewards for external parties performing security tests on the organizations assets

#### Pen testing vs Vulnerability assessment 

- pen testing provides assurance in your vulnerability assessment and management process
- the aim should be to use your findings to improve the vulnerability assessment and management process

#### bug bounties vs pen testing

![[Pasted image 20250116121116.png]]

#### who conducts pen testing

red team
- offensive team, attackers
- attacking in any way they can
	

purple team
- cooperation of teams to improve defense and attacking ability

blue team
- defensive team, defending 
- defending against the red team as best they can

#### penetration testing scenarios 

- vulnerability identification in bespoke software
	- Used to give feedback to developers on coding practices which prevent the vulnerabilities identified
- scenario driven testing aimed at identifying vulnerabilities
	- The pen testers explore a particular scenario to discover if it leads to a vulnerability
- scenario driven testing of detection and response capability
	- The aim is to also gauge the detection and response capabilities your organization has in place

#### limitations of pen testing

- not intended to be a comprehensive evaluation of security, many security issues and configuration problems may not be identified
- the amount of information that can be gathered in a given time period is limited
- if the limited nature of a penetration test is not understood, the test can given the target organization a false sense of security

#### legal issues of pen testing

- the main thing that differentiates a pen tester from attacker is permission, important consent is obtained from 3rd party hosting environments or equipment also
- what constitutes authorization and who can authorize such access can quickly get mucky

#### stages of pen testing 

- Planning: identify rules, finalize and document management approval, set test goals
- discovery: reconnaissance, scanning, enumerations
- Attack: gaining access, escalating privileges, system browsing
- reporting: lack of security policy, poorly enforced policy, misconfiguration, software reliability, failure to apply patches

![[Pasted image 20250116122626.png]]


#### scoping the pen test

- risk owners should outline any areas of special concern
- technical staff should outline the technical boundaries of the organization's IT estate
- the pen test team should identify what testing they believe will give a full picture of the vulnerability status
- outline issues which might impact testing, like out of hours testing


#### plan of action document 

- technical boundaries of the test
- the types of tests expected
- the timeframe and the amount of effort necessary
- optionally the scenarios or specific use cases to test
- the pen testing teams requirements
- compliance or legislative requirements that the testing must meet
- any specific reporting requirements

#### rules of engagement ROE
• Detailed guidelines and constraints regarding
the execution of information security testing.
• The ROE is established before the start of a
security test.
• Gives the test team authority to conduct
defined activities without the need for
additional permissions.
• Non-Disclosure Agreement (NDA)
• Get Out Of Jail Free Card


### discovery stage
#### Reconnaissance 
• Physical environment and access
• Network port and service identification
• Host name and IP address information
• Employee names and contact information
• Analysis of collected data to discover potential vulnerabilities

### Attack stage

![[Pasted image 20250116123453.png]]



#### vulnerabilities exploited during pen testing

- misconfiguration security settings, particularly insecure default settings
- flaws in the kernel code of an os that enforces the overall security model for the system
- insufficient input validation that leads to attacks such as buffer overflows or sql injections 
- race conditions that occur during the time a program or process has entered a privileged mode
- improperly configured descriptor or symlink

#### social engineering attacks

- Phising/smishing: A message/email pretending to be from someone
the victim knows. The message have a link that when clicked it
would infect the victim’s device.
- Baiting: A USB stick labelled as confidential is dropped in the
parking lot If inserted, it installs malware.
-  Pretexting: A scammer contacts the victim pretending to be IT
support offering technical help citing a problem.
- Tailgating: The attacker follows an employee into a building that
normally requires access through a badge. 


### reporting stage

• Lists any security issues uncovered
• An assessment by the test team as to the level
of risk that each vulnerability exposes the
organisation or system to
• A method of resolving each issue found
• An opinion on the accuracy of your
organisation's vulnerability assessment
• Advice on how to improve your internal
vulnerability assessment process