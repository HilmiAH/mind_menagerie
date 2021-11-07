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

## 8. Techniques and Methods
# 9. Security Management
# 10. Secure Software
# 11. (OPTIONAL) Emerging Security Issues 