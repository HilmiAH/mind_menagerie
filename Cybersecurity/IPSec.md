provides confidentiality and/or integrity to network packets
- C: data encryption
- I: hash functions

verify the sources of packets using authentication
prevent *replaying* packets using sequence numbers (or nonce, timestamp,etc.)

IPSec Modes
1. Choose mode
- Transport Mode
	- host-to-host
	- protects upper level protocols
	- IP header, IPSec header, rest of packet
- Tunnel Mode
	- end routers
	- between gateways or from end-station to gateway
	- New IPSEc header, IPSec header, IP header, rest of packet
	- difference is now the new headers go before IP header instead of after
2. Choose protocol
- Authentication Header (AH)
	- Authentication, data integrity
	- **No Encryption/Confidentiality**
	- IPSec and IP headers in clear text
- Encapsulating Security Payload (ESP)
	-  Data origin authentication, data integrity, data confidentiality
	-  **No IP header authentication**
	-  **Extra padding**
	-  Data fields will be encrypted
	-  The ESP IPSec header and everything in between is authenticated (but IP header is excluded)
-  Satisfies different security requirements

- Higher layers can remain ignorant of security at lower layers.
- Not aware of applications requirements, which may result in messing with performance requirements needed.
- Needs to be ordered (opposite of IP design)