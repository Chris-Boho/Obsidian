### Authentication
- Verification of identity claim
	- you are who you say you are

- Three Kinds of Secrets:
	1. Something you know
		- a password
	2. Something you are
		- fingerprint 
		- voice scan
		- iris scan
		- face scan
	3. Someting you have
		- smart card
		- smart phone

### Authorization
- what a user can do depends on who they are
- usually must refer to policy specification
	- what resources can be accessed by a given person

### Access Control
- policy specify how entities can interact with resources
	- who can access what
- Access Control Primitives:
	- Principal: user of a system
	- Subject: entity that acts on behalf of principals
		- software program
	- Object: resource acted upon by subjects
		- files 
		- sockets
		- devices
		- OS APIs

### Discretionary Access Control (DAC)
- access rights propogate and may be changed at subject's discretion
- means of restricting access to objects based on the identity and a 'need to know 'basis

### Mandatory Access Control (MAC)
- access of subjects to objects is based on a system-wide policy
- denies users full control over resources they create

## Unix-Style Permissions
- based around the concept of owners and groups
	- all objects have an owner and a group
	- permissions assigned to owner, group, and everyone else
- Users identified by user name (UID) and group name (GID)
	- authenticated by password

### Setting permissions
- `chmod [who] < +/- > <permissions> <file1> <file2>`
- who: 
	- omitted -> user, group, and other
	- a -> user, group, and other
	- u -> user
	- g -> group
	- o -> other
- permission:
	- r -> read
	- w -> write
	- x -> execute
- Examples:
	- amin@DESKTOP:~$ `chmod ugo-rwx cs2550`
	- amin@DESKTOP:~$ `chmod go-rwx submission.py`
	- amin@DESKTOP:~$ `chmod u-rw submission.py`
	- amin@DESKTOP:~$ `chmod +x grade`

- `chmod ### <file1> <file2>`
	- `###` corresponds to owner, group, and other
	- each value encodes read, write, and execute permissions
		- 1 -> execute
		- 2 -> write
		- 4 -> read
		- 7 -> set as all
- Examples: 
	- amin@DESKTOP:~$ `chmod 000 cn5079`
	- amin@DESKTOP:~$ `chmod 100 submission.py`
	- amin@DESKTOP:~$ `chmod 777 grade`