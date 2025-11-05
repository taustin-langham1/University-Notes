
 station01@anshar.world
 password123

http://asherah.anshar.world

Baseline:

reactor power 100%

RX_FuelTemp = 948 (red)
many cool temps yellow (560-80)
CD_SteamTemp (306)

RX press = red ~15m
SG / TB press = green 6m

reactor PW at ~100%

drastic changes in the reactor power set point cause over and under corrections - e.g., 70 -> 100, will push PW to 107pw 

Zone 2a is process control

10.2.1.X
10.2.1.10 sends the most packets (6MB) - followed by 10.2.1.1 (3MB)

q0.10100


identifiers and values of 5 OPC UA variables
that controllers are reading from the OPC UA server
1 id: CTRL_RC1FlowSetpoint 
2 id: CTRL_ PZLevelSetpoint  
3 id: CTRL_CDLevelSetpoint 
4 id: CTRL_RXPowerSetPoint 
5 id: RX_ReactorPower 

baseline 31 packets 
spikes a few packets when change to the reactor setpoint 



Ethernet
IPv6 -> ICMP v6
IPv4 -> TCP -> OpcUa Binary Protocol







