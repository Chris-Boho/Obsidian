### Ping
- low level network utility
- sends "ping" ICMP message to a host on the internet
- destination responds with a "pong"
- if ping message is too long, it causes a crash

#### DoS
- prevent users from being able to access a service or computer
- attack on availability
- possible vectors:
	- exploit bugs that lead to crashes
	- exhaust the resources of a target
- easy to perform
- incredibly difficult to mitigate
- asymmetric:
	- relatively small numer of resources are required by an attacker to cause a significantly greater number of resources to fail

### DDoS
- some fueled by volunteers
- most fueled by botnets

### Smurfing
- exploit characteristics of broadcast networks
- ICMP protocol does not include authentication
- example of reflection or amplification attack
- steps:
	-   First, the malware creates a network packet attached to a false IP address - a technique known as "spoofing."
	-   Inside the packet is an ICMP ping message, asking network nodes that receive the packet to send back a reply
	-   These replies, or "echoes," are then sent back to network IP addresses again, setting up an infinite loop.

### Mitigations 
- avoid being an amplifier
- clean up amplifiders
- get vendors to issue patche that disable certain services or features by default
- if UDP service, authenticate sources of packets
- reduce attack surface area
	- limits the options for attackers
	- focus building protections in a single place