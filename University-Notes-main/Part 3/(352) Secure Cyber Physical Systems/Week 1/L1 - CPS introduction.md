

"Cyber-physical Systems, (CPSs) are engineered systems that are built from, and depend upon, the seamless integration of computation, and physical components"

E.g., a nuclear power plant
- tightly integrated physical and digital components
- real time sensing and control
- high assurance requirements

#### Characteristics of a CPS

- control - CPSs observe and attempt to control variables in the physical world
- real-time - CPSs have timing requirements to sense the world and actuate a physical element of the system within certain time bounds
- specialised - CPSs are specialised to the task they need to perform
- interaction - CPSs will interact with IT systems (over a network) and other CPSs (over a network or via the physical environment)

#### Requirements of a CPS

- safety - minimise likelihood of harm
- reliability - no failures
- Fail safe - fail safely
- Fail tolerant - continue operating
- Resilience - recover quickly
- Robust - handle uncertainty 

#### Being safe is insufficient to be secure

- different aims:
	- safety - protect subjects form the system
	- security - protect the system from malicious intent
- safety does not aim to handle intentionally malicious actions
- safety remains critical for CPSs
- being secure is also insufficient to be safe

#### CPS Security Differs from IT Security 

- IT security (typically) focuses on data security
	- confidentiality - prevent unauthorised access of data
	- integrity - prevent unauthorised medication of data
	- availability - ensuring that access to data is timely and reliable
- CPS Security (typically) focused on impacts to the physical interaction
- This does not mean:
	- CPS do not have data security concerns
	- These are the only classes of threats that either system is subject to


#### CPS Architecture

- Sensors monitor the environment - report to controller

- Controller instructs actuators to change the physical state based on sensor data and supervisor commands

- Actuators change environment state via physical processes which get observed by the sensors 


#### CPS Architecture - Attack Points
 
 ![[Pasted image 20251008091026.png]]


#### Why this matters?

- operational technology (OT) and Industrial Control Systems (ICS) are a focus of attacks
	- These systems are critical to the UK's infrastructure
	- Attacks on them lead to nationwide impacts
- CPS are designed for safety, reliability and long continual operation
	- security has not been a particular concern until recently
	- ensuring the security of CPSs can be expensive


