#### Learning Objectives 

- understand the need and nature of digital forensic procedures

- Describe each phase in the data gathering process

- Appreciate the importance of documented procedures which define a forensic investigation

- comprehend individual elements which male up a chain of custody trail

- differentiate between live and post-mortem forensics including the advantages and limitations of each

#### Glossary:

**PLC** - programmable logic controller

**HMI** - human machine interface

**ICS** - Industrial control system

**MD5** - message digest (5th revision) 128-bit (16-byte) output

**SHA1** - secure hash algorithm 160-bit (20 byte) output

**CRC** - cyclic redundancy check


## Software for investigations

•FTK Imager – imaging drives and creating bit-for-bit copies

•Autopsy – analyzing digital evidence (deleted file recovery)

•Cellebrite/XRY – mobile forensics

•EnCase/X1 Social Recovery – advanced tools for larger investigations

•Write Blocker – to ensure no modification during acquisition

•Wireshark – for network traffic analysis


## Non-Social Engineering Attacks

- Denial of Service (DoS attacks)

- Man in the Middle (MITM attacks)

- Ransome wear

- SQL injection

- Session hijacking

- Brute force attacks

- Malware attacks


## Digital forensics 

- digital forensics is the identification, collection, preservation, and analysis of digital artefacts

- a digital forensic analyst must:

	- *strategize a method and identify assets relevant to investigation*
	- *collect evidence to support criminal investigations*
	- *preserve the integrity of the information*
	- *analyze evidence to support or refute events*
	- *guarantee chain of custody procedures have been followed*

## Chain of Custody

-  A document verification of where evidence has travelled, which personnel handled it 
- Prevent substitution, tampering, damaging, altering, contamination, misplacing or falsifying evidence
- Logs used to record changes in custody at each transfer, providing a comprehensive record of the evidence's movement 
- Maintaining a robust chain of custody upholds the credibility of evidence in legal proceedings and scientific investigations

### Chain of custody: Form

![[Pasted image 20250220131318.png]]


## Key forensic stages

**Identify resources**

**Preservation of data**

**Analysis of data** - reverse steganography, data carving 

**Documentation**

**Presentation** - evidence to support judicial process


## Goal of Forensic Investigation

- determine who's involved

- determine the incident's underlying causes

- Determine whether the law has been broken

- Separate fact from fiction

- correct the mistake



## Pre-Investigation Strategy

**Considerations prior to forensic analysis of a component in an ICS**

- Could the investigation itself, compromise or effect system safety?
- how long can the system remain offline while forensics take place?
- What documentation will be followed and to who will this be reported?
- When do you involve national authorities?
- How will data be acquired? 

## Targets of Forensic Investigation

- static corporate assets
- Mobile device forensics
- Internet of things
- Network forensics
- Cloud forensics

## Cloud Forensics

**Data sovereignty** - Data subject to the laws and of the country of location
**Government surveillance** - authority to access data stored within their borders for national security 
**Audit Compliance** - Based on the jurisdictions where their data is stored
**Data transfer** - jurisdictions restrict cross border transfer of data
**Data localization laws** - some countries require certain types of data to be stored within their borders


## Visual inspection

- machine serial numbers, make, model, ...
- Note any removable media and foreign objects
	- usb devices plugged in?
	- peripherals used (keyboard? mouse? Ethernet cable?)
	- Suspicious hardware implants?
- note any physical damage to equipment
	- indications of tampering/manipulation of equipment
- Take photographs (document, document, document!)

## Live forensics

- **Live forensics** - carried out when the system is running:
	- access to volatile memory (RAM, cache, ect.) which is lost upon system shut down
	- Risky - can alter the system state and potentially lose other evidence
	- Risks altering data on the non-volatile storage media (SSD,HDD)
	- If the machine is on, extract volatile memory (RAM, cache) if possible
	- offers an insight into the state of the machine at time of seizure

## Post-Mortem Forensics

- **Post-mortem** - carried out when the system is turned off or when media is removed to other machines for analysis
	- if the machine is powered off take it and extract the storage media
	- an image (static, logical copy/snapshot) of the storage media can be taken using forensics software
	- Imaging and analysis of mass storage devices (SSDs, HDDs, Memory Cards, USBs)
	- Write blocker for access to avoid altering data
## Challenges to Data Acquisition

![[Pasted image 20250220140721.png]]


## Orders of volatility

1.CPU, cache, and register contents

2.Routing table, ARP cache, process table, kernel statistics, network connections

3.Memory

4.Virtualized systems

5.Temporary file system/swap space

6.System & security device logs

7.Hard disk data (Post)

8.Remotely logged data

9.Physical media (CDs, Back-up tapes, etc) 

## Considerations

- how are artifacts recorded or packages
	- bag and tag
	- photographing
	- RAM dumping

- where will evidence be analyzed and how is it securely transported
- How will evidence be stored once transported?
- How will the forensic process be controlled?
- where is documentation stored?

## Forensics Anticipation

**Logging**
if devices or systems have logging capability, this should be active if possible and does not endanger the operation of the system

**Monitoring**
Network monitoring tools used if possible. May require commercial off-the-shelf (COTS) monitoring solutions to be configured for ICS

**Baselining**
Hardware and software configurations should be backed-up, and copies of verified PLC logic should be stored for future reference 

## Volatile memory collection

PLC status lights (RUN/STOP mode indicators, fault indicators, flashing lights on Ethernet ports) should be recorded
- *use a slower shutter speed/film to avoid syncing with the LED's*

Document HMI status and display including HMI alarm list

Collect diagnostics information via workstation

Make note of device systems clock
	is it in sync with the other systems?

## Non-volatile memory colleciton

•Physical memory should be removed and replaced

- PLCs and HMIs that use SD cards should have physical copies

•Back-up Network monitoring tools and packet captures

- can be used later to align network traffic to PLC reconfiguration

•If possible, replace whole device

- not always easy for industrial equipment

## Documentation

Incident reporting should be outlined in your incident response plan:

When should reporting take place?

- less-formal updates vs formal post-mortem forensics reporting

Who receives the report?

- dependent on personnel structure, severity, investigation stage

- do the board of directors or shareholders need to be informed?

Report incident to national and/or international authorities?

- legal authorities, government ministers, International Atomic Energy Agency

