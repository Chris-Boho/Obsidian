## Chapter 4

### Key Network Layer Functions
- forwarding - data plane: 
	- move packets from router's input to appropriate router output
- routing - control plane: 
	- determine route taken by packets from source to destination
- ![[Pasted image 20221208180820.png]]

### Longest Prefix Matching
- forwarding table lookup: 
	- destination based matching
- a destination my match multiple prefixes
- longest matching prefix is selected

### Scheduling Mechanisms
- scheduling: choose next packet to send on link
- different scheduling mechanisms: 
	- FIFO
	- priority 
	- round robin
	- Weighted Fair Queuing

### IP Datagram Format
- ![[Pasted image 20221208181855.png]]

- IP Addressing:
- CIDR: 
	- Classless InterDomain Routing
	- subnet portion of address of arbitraty length
	- address format: a.b.c.d/x, where x is # of bits in subnet portion of address

### DHCP: Dynamic Host Configuration Protocol
- goal:
	- allow host to dynamically obtain its IP address from network servers when it joins network
		- can renew its lease on address use
		- allows reuse of addresses 
		- support for mobile users who want to join network
- Overview:
	- host broadcasts "DHCP discover" msg
	- DHCP server responds with "DHCP offer" msg
	- host requests IP address with "DHCP request" msg
	- DHCP server sends address "DHCP ack" msg

### Nat: Network Address Translation
- NAT router must:
	- outgoing datagrams: 
		- replace source IP address, port # of every outgoing datagram to NAT IP address, new port #
		- remote clients/servers will respond using NAT IP address, new port # as destination address
	- remember in NAT translation table
		- every source IP address, port # to NAT address, new port # translation pair
	- incoming datagrams:
		- replace NAT IP address, new port # in destination fields of every incoming datagram with corresponding source IP address, port # stored in NAT table 

### IPv6 Datagram Format
- motivations:
	- more IP addresses: 128-bit
	- speed processing/forwarding: 
		- fixed length header
		- no fragmentation allowed
		- checksum removed
	- facilitate QoS
- ![[Pasted image 20221209145941.png]]

### OpenFlow Data Plane Abstraction
- flow: defined by header fields
- generalized forwarding: simple packet handling rules
	- Pattern: match values in packet header fields
	- Actions: 
		- for matched packet: 
			- drop, forward, modify, matched packet or send matched packet to controller
	- Priority: disambiguate overlapping patterns
	- Counters: #bytes and #packets

### OpenFlow Abstraction
- match + action: unifies different kinds of devices
- Router:
	- match: longest destination IP prefix
	- action: forward out a link
- Switch:
	- match: destination MAC address
	- action: foward or flood
- Firewall:
	- match: IP addresses and TCP/UDP port numbers
	- action: permit or deny
- NAT:
	- match: IP address and port
	- action: rewrite address and port

## Chapter 5

### Network Layer Functions
- Two approaches to structuring network control plane:
	- per-router control (traditional)
	- logically centralized control (software defined networking)

### Dijsktra's Algorithm
- https://youtu.be/_lHSawdgXpI

### Distance Vector Algorithm
- ![[Pasted image 20221209163727.png]]

### Count to Infinity
- problem:
	- bad news travels slowly
	- many iterations before algorithm stabilizes
- poisoned reverse:
	- if Z routes through Y to get to X:
		- Z tells Y its (Z's) distance to X is infinite, so Y won't route to X via Z
	- ![[Pasted image 20221209163913.png]]

### Hierarchical Routing
- aggregate routers into regions known as "autonomous systems" (domains)
- intra-AS routing:
	- routing among hosts, routers in same AS (network)
	- all routers in AS must run same intra-domain protocol
	- routers in different AS can run different intra-domain routing protocol
	- gateway router: at "edge" of its own AS, has links to routers in other AS's
- inter-AS routing: 
	- routing amoung AS's 
	- gateway perform inter-domain routing as well as intra-domain routing

### Open Shortest Path First (OSPF)
- open protocol based on Link State Algorithm
- router floods OSPF link-state advertisements to all other routers in entire AS
- security: all OSPF messages authenticated
- ECMP: equal-cost multiple paths
- two-level hierarchy: local area, backbone

### Border Gateway Protocol (BGP)
- two types of BGP (TCP) sessions
	- eBGP: between neighboring AS
	- iBGP: inside same AS
- router may learn about more than 1 route to destination AS, selects route based on:
	- local preference value attribute: policy decision
	- shortest AS-PATH
	- closest NEXT-HOP router: hot potato routing
	- additional criteria

### Software Defined Networking (SDN)
- SDN: logically centralized control plane
	- 