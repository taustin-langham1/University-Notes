How does retrofitting existing CPSs, or revising them to add connectivity, change their threat landscape?

Connected Vehicles 
Industry 4.0 and industrial IoT

## Vehicles

### CAN Bus
#### - Historical

- historically no encryption or authentication
- bus assumed to be a 'walled garden'
- if an adversary gets access to the bus, then they can have a large influence over a vehicle
	- gain control over an electronic control unit (ECU) can allow attacker to influence system
	- physical attacks to connect devices to the OBD-II port
- potential for there to be vehicles in this state on the road that have not been updated

#### - Current

Encryption and authentication on the bus is becoming common place 
challenge of:
- backwards compatibility
- performance impact of encryption/decryption/authentication on timing constraints

### Vehicle Communication

- vehicles communicating is a key part of 
	- Connected and autonomous vehicles
	- Connected and autonomous mobility

#### Why communicate?

- broadcast safety messages
- inform other vehicles of events
- manage autonomous platoons
- logistics and freight management
- Other: Stream video between vehicles

#### What is in a Cooperative Awareness Message?

- Sent by a vehicle every 100-1000ms
- contains information used to avoid unsafe scenarios
	- GNSS coordinate
	- Speed
	- Heading 
	- Acceleration
- Other useful information
	- Vehicle dimensions
	- Light status
	- Is it carrying dangerous goods?
- Messages are intentionally unencrypted
- protected with a digital signature for non-repudiation and integrity

#### What is in a Decentralised Event Notification Message?

- Sent by a vehicle when an event occurs
- Contains information about the event
	- when and where 
	- area of relevance
	- event duration
- DENMs can be forwarded to other vehicles aware of the event
- Messages are intentionally unencrypted
- protected with a digital signature for non-repudiation and integrity

- traffic condition
- accident
- roadworks
- adverse weather conditions
- hazardous location
	- surface conditions
	- obstacle
	- animal
human presence on road
wrong way driving


## Industry 4.0, and Industrial IoT (IIoT)

#### Industry 4.0

characterised by:
- increase complexity or robotically automated tasks
- data gathering/analysis/visualisation about industrial system
- application of ML for efficiency / predictive maintenance
- building digital twins of a system
retrofitting of existing equipment
- new connectivity
- new capabilities
- not previously connected equipment

#### Interactions between Human, Cyber and Physical Elements of a System

![[Pasted image 20251119093747.png]]

#### Retrofitting Changes the threat model

OT systems will typically use a layered security architecture

Boundaries between layers become less clear when retrofitting industrial equipment with sensors and connectivity

- Default credentials
- lack of updates
- new ways for adversaries to observe a system
- potential for poor physical security controls
- complexity of using security mechanisms such as TLS or link-layer encryption

## Jaguar Land Rover (JLR) Attack

- proactively shut down systems to mitigate the impact of the attack
- no detailed breakdown of attack yet
- suspected combination of 
	- phishing / credential theft - initial access 
	- ransomware
- impact:
	- production delayed for 5 weeks
	- knock-on impact to supply chain
	- estimated £1.9bn impact

## Summary

• There is a push to integrate connectivity into systems where it was
previously absent
• Gather data about the system’s use
• Predictive maintenance
• New capabilities (e.g., automation)
• Extend system lifetime
• The attack surface of the system changes significantly
• Many organisations which were not technology focused need to learn
how to secure their connected estate