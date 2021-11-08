# 1. Intro to Cybersecurity
This lecture gives an overview of the content of the unit.
## Terms
- Risk
- Vulnerability
- Exploitation
- Threat
- Asset
- Security
	- Confidentiality
	- Integrity
	- Availability
	- Extras:
		- Authentication
		- Non-repudiation
- Risk control/management
- Security policy
- Security management
## Defense Overview
Actions against cyberattacks:
- Acceptance
- Avoidance
- Transfer
- Mitigate
- etc.

Three types of defense in general
- Prevention: access control, firewall
- Detection: IDS, forensics, auditing
- Reaction: intrusion tolerance

# Cryptography
## 2.
## Terms
- Plaintext
- Ciphertext
- Cipher algorithms
- Keys
- Encrypt
- Decrypt
## Principles of Ciphers
- Substitution
- Transposition
## Classic Ciphers
### Caesar cipher
### Monoalphabetic cipher
### Vigenere cipher
### Transposition cipher
## Modern Ciphers
### AES
### DES
### Modes for AES and DES
- ECB
- CBC
- CFB
- OFB
- CTR
## Cryptanalysis
- Brute-force attack
- Cryptanalytic attacks
- Results
## Security of Ciphers
- Computationally secure
	- Cost to break > cost to encrypt
	- Time taken > useful lifetime
- Provably secure: proven to be equivalent to hard problem
- Unconditional security
	- Cannot succeed given infinite resources
	- Only example: one-time pad
## 3.
## Public key cryptography
## RSA
Integer factorization problem
## DH
Discrete logarithm problem
## Hashing
## Blockchain
### Cryptocurrency
## ECC
## Symmetric vs Asymmetric Key Cryptosystems
# Cyberattacks
## 4. Attack Classifications
- Attack trends
- Classification
	- Social engineering
		- Phishing
		- Pharming
		- Offensive USB
		- Mitigation
	- Cracking
		- Password cracking
		- Packet sniffing
		- Mitigation
	- Malware
		- Types
			- Virus
			- Worm
			- Malvertising
			- Spyware
			- Trojan
			- Rootkits
			- Botnet
		- Mutations
			- Oligomorphic
			- Polymorphic
			- Metamorphic
		- Protection
			- Antivirus
			- Access restriction
				- Remote access control
				- Firewalls
				- Email filtering
		- Worm vs Virus
	- Network-layer attacks
	- Web-based attacks
	- (D)DoS
	- Zero-day
		- Detection
		- Keeping up-to-date
## 5a. Network Attacks
TCP layers:
- Application - n/a, data
- Transport - datagram, TCP|Data
- Internet - packet, IP|TCP|Data
- Network Access Layer - frame, MAC|IP|TCP|Data

Kinds of network attacks:
- Sniffing
- Spoofing
	-	TCP
	-	IP
- Hijacking
	- TCP Session Hijack
- Remote Access
	-	Reverse Shell
	-	Forward Shell
- Denial of Service
	- Volume-based
	- Protocol
	- DDoS
		- Reflection attack
		- Amplification attack
	- Prevention
		1. Prevention and preemption: patch known vulnerabilities and flaws
		2. Detection and filtering: update firewall rules and IDS
		3. Trace-back and identification: conduct forensics and analysis
		4. Reaction: review security control and update

## 5b. Buffer Overflows
Memory layout of stack
C/C++ vulnerabilities
Exploit steps
Prevention
- Use safer C/C++ routines and avoid vulnerable ones
- Use safer programming languages
- Check legacy code for BoF
- Security controls
	- Non-executable stacks (i.e. Data Execution Prevention, DEP)
	- Address Space Layout Randomization (ASLR)
- Tools:
	- Scanning source code for routines
		- Static source code checkers
	- Dumping binary code to look for character strings
## 6a. Web-Based Attacks
Sql Injections
XSS
## 6b. Ransomware
# Defense Mechanisms
## 7a. Protocols
HTTPS
SSL
IPSec
-	AH
-	ESP
VPN
## 7b. Tools
Firewall
IDS
- ID models
	- Misuse detection (signature or knowledge-based)
	- Anomaly detection (behavior-based)

__   | Misuse                                                             | Anomaly
---- | ------------------------------------------------------------------ | ---------------------------
Pros | accurate, setup ease/speed                                         | fast, detect new variations
Cons | slow, cannot detect variations, signature database update required | false positives, requires profiling behaviors

- IDS placements
	- Host-based (HIDS)
		- Sits inside host
		- Monitor system usage
		- OS dependent
	- Network-based (NIDS)
		- Sits in network at a location
		- Capture/monitor packets
		
Wireshark
- Applications:
	- Emotet trojan
	- Trickbot trojan

## 8. Techniques and Methods
Vulnerability scanning
- ping/ICMP scan (server scanning)
- Port scanning 
	- TCP scan 
		- Initiate 3-way handshake
			- fast/no privilege
			- easily detectable (likely blocked)
		- Stealth scan 
			- TCP SYN scan (aka, half-open scanning)
				- Send SYN packet
				- Get SYN+ACK packet = open
				- Get RST+ACK packet = closed
			- TCP FIN scan
				- send FIN
				- no response = open
				- RST+ACK = closed
			- Additional techniques
				- Fragmentation scan
				- Reverse ident scan: use ident protocal to extract connection info
				- FTP bounce attack: manipulate FTP server to redirect files
	- UDP scan
		- send UDP packet
			- no response = open
			- CMP "Unreachable" packet received = closed
- Vulnerability databases: contain Common Vulnerabilities and Exposures (CVE) + security metrics
- requires continuous effort to discover and mitigate vulns.
- difficult to address new/unknown vulns.
- global effort

Sandboxing
- Confinement
	- Hardware (HW, air gap)
	- Virtual Machines: isolate multiple OS on single HW
	- System call interposition: isolate process in an OS
	- Software Fault Isolation (SFI): isolate threads from sharing address space
	- Application specific (e.g. browsers)
- examples:
	- chroot and su
		- **ch**ange **root** directory
		- **s**with **u**ser to guest
		- "jails" user within `/tmp/guest`
		- need copy of utilities
		- can priv-esc if you have process w/ root priv in jail
		- cons:
			- all or nothing access to filesystem
			- need access to files outside of jail
			- can still access the network (sandboxed locally but not for the network)
		- DO NOT USE
	- SFI
		- separate applications to diff. address spaces and add checks before memory operations by...
			- partition memory into segments
			- locate unsafe instructions
				- add safety instructions for mem. access
				- add guards before unsafe instructions at compile time
				- validate guards when loading them
			- reconstruct code for safety (by changing the machine code)
			- add guard zone to avoid calculations for register/offset addressing
			- untrusted applications should only
				- jump within its code segments
				- write within its data segments
			- pros (can be cons depending on context):
				- little processing overhead (4%)
				- confines writes and control transfers
				- prevents privileged execution
			- cons:
				- not designed so difficult to impl. for x86 architectures/instruction set
					- variable len. instr., many more mem. instr.

Steganography: hiding messages within data
- Text: i-th character of every line, unusual white-space (increased size)
- Image(audio, etc.): least significant bit (LSB) of colour byte (3 bits/px), BMP images used for lossless compression
- Steganalysis: know what to look for and use tools, but crytography and steg are usually combined

Moving Target Defense (MTD)
- continuously/randomly change the attack surface
- different layers
	- application: code regen/diversify
	- transport: routing node redundancy
	- internet: IP shuffle/virtualise
	- MTD shuffle: changes config (conn. and depend.) of system while operations is same
		- delay recon, and break ongoing attack
		- e.g. Openflow Random Host Mutation: virtual IP w/ x frequency
		- issues, shuffle may...
			- produce insecure system state
			- violate security requirements
			- not be be feasible (performance)
			- not applicable (homogeneous network/system)
			- frequency/strategy unknown/TBD
	- MTD diversity: rotate diff. components/services w/ same functionality.
	- e.g. compiler generated
	- issues, variants may...
		- be more vuln.
		- cost more to impl.
		- more downtime
	- MTD Redundancy: ensure availability, can be used with other MTD techniques
	- e.g. DDoS prevention
	- Issues:
		- resource constraints
		- ineffective against conf. and int. attacks
		- increasing redundancy has diminishing returns on availability
# 9. Security Management
# 10. Secure Software
# 11. (OPTIONAL) Emerging Security Issues 