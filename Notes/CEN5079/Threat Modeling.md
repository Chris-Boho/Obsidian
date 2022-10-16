# Threat Modeling
- Proces of systematically identifying threats faced by the system

1. Identify things of value that you want to protect
2. Enumerate the attack surfaces
3. Hypothesize attackers and map them to
	- Things of value they want from (1)
	- their ability to target vulnerable surfaces from (2)
4. Survery mitigations 
5. Balance costs versus risks

### Identifying 
- saved passwords
- personally identifiable information
- credit card data
- bank accounts
- sensitive business documents

### Enumerate Attack Surface
- steal the device and use it
- direct connection via USB
- Bluetooth / NFC
- passive eavesdropping on network
- active network attacks 
	- MiTM
- physical security 
- local exploits
- local network connection 
- remote exploits

### Hyptothetical Attacker
- Thief
	- steals phones 
	- goal: device itself / financials apps on device

### Mitigations 
- Strong passwords
- device encryption
- remote tracking and wiping
- physical security 
- OS and Software patches
- firewall

### Balancing Cost and Risk
- access the likelihood of different attacks
- compare to the cost of mitigations

## Stride
- Designed to model and mitigate threats against software

1. Identify Assets
2. Create architecture overview
	- diagrams that map out the target system
3. Decompose the application
	- uncover vulnerabilities in design, implementation, or deployment
4. Identify the threats
	- Keep the goals of attackers in mind
5. Documents the threats
6. Rate the threats
	- prioritize and address the most significant threats first