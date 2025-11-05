
## Industrial Control System Communications

1. Approaches to communication for industrial control systems to
understand the characteristics of these protocols

### The modbus protocol

developed by modicon
free and os
most common protocol in SCADA and ICS networks

- can modbus over TCP/ip, RTu, TLS - secure communication over the internet
#### Modbus over TCP/IP

 modbus RTU is a serial ICS communication protocol for use with programmable logic controllers
Modbus TCP/IP is an application-layer network protocol that implements the serial
Modbus protocol within TCP/IP
Uses Client/Server communication model
The server listens on TCP Port 502
If configured as a gateway, a Modbus TCP/IP server can forward Modbus TCP/IP
messages to Modbus RTU devices by matching a Unit ID to a Modbus RTU
attached Server ID

![[Pasted image 20251023121609.png]]

• Modbus is a Client/Server protocol
• Only Clients can initiate conversation
• Valid Server IDs 1-247
• The Server ID must be unique per bus
• Servers will generate an error when
improperly addressed
• Clients must wait for responses

![[Pasted image 20251023121652.png]]
## How OPC UA works to support your work in the upcoming lab exercises

### OPC UA

higher level than modbus - used for plc interaction
lots of refinement to OCPUA - include lots of modern features

- a platform independent architecture for machine-to-machine communication in industrial automation environments
- improvement on its predecessor, OPC DA (Data Access)
	- DA was built on the microsoft-only distributed component object model (DCOM)
	- UA can be implemented on cloud-based infrastructure or embedded controllers
- Currently supports both Client/Server and Publish/Subscribe communications

![[Pasted image 20251023120434.png]]

### MQ Telemetry Transport (MQTT)

- OASIS standard messaging protocol for the Internet of Things
- Ideal for connection remote devices with a small code footprint and minimal network bandwidth
- used publish/subscribe messaging pattern
- supports TLS encryption and client authentications


### Domain Specific Industrial Protocols


### Wireless Industrial Protocols

