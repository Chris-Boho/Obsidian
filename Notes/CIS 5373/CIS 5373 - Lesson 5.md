## Defining Access Control 
- process of protecting a resource so that it is used only by those allowed to
- prevents unauthorized use
- mitigations put into place to protect a resource from a threat 

## Four Parts of Access Control
- Identification - who is asking to access the asset?
- Authentication - can their identities be verified?
- Authorization - what, exactly, can the requestor access? And what can they do?
- Accountability - how are actions traced to an individual to ensure the person who makes data or system changes can be identified?
	- logging
	- audits 
	- 2FA

---

- Policy Definition Phase: who has access and what systems or resources they can use
	- tied to the authorization phase
- Policy Enforcement Phase: grants or rejects requests for access based on the authorizations defined in the first phase
	- tied to identification, authentication, and accountability

---

## Two Types of Access Control
- Physical: controls entry into buildings, parking lots, and protected areas
	- smart cards
- Logical: controls access to a computer system or network 
	- usernames and passwords
	- biometrics
	- tokens

- Information Security is a delicate balance between the risks and controls
	- if the controls are too strong, then users will complain or find a way around it
	- if the controls are too weak, then the risks of being hacked are higher

## Access Control Policies
- Users: people who use the system or processes
- Resources: protected objects in the system
- Actions: activities that authorizeed users can perform on resources
- Relationships: optional conditions that exist between users and resources

## Authentication Types
- Knowledge - something you know
- Ownership - something you have
- Characteristic - something unique to you
- Location - somewhere you are
- Action - something you do / how you do it

## Four Models of Access Control
- Discretionary Access Control (DAC)
	- 'the right to decide something based on one's own judgement'
- Mandatory Access Control (MAC)
	- determine the level of restriction by how sensitive the resource is 
	- system and owner decide to allow access
	- MAC stronger than DAC
- Nondiscretionary Access Control 
	- access rules are closely managed by security administrators, not system owner or users
	- sensitive files are write-protected for integrity and readable only by authorized users
	- more secure than DAC
	- ensures that system security is enforced and tamperproof
- Rule-based Access Control
	- explicity rules grant access

## Threats to Access Control
- gaining physical access
- eavesdropping by observation
- bypassing security
- exploiting hardware and software
- reusing or discarding media
- electronic eavesdropping
- intercepting communication
- accessing networks
- exploiting applications

## Effects of Access Control Violations
- loss of customer confidence
- loss of business opportunities
- new regulations imposed on the organization
- bad publicity
- more oversight
- financial penalties

## Decentralized Access Control
- access control is in the hands of the people closest to the system users
- password authentication protocol (PAP)

---

- IaaS - infrastructure as a service
- PaaS - platform as a service
- SaaS - software as a service