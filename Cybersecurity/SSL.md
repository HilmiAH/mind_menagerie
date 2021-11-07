- Used in HTTPS
- Secure Socket Layer (port 443 usually)
- provides encryption and authentication of the server
SSL Handshake:
	1. Establish details
		1. Client
			- Key exchange (RSA, DH, etc.)
			- Cipher (3DES, AES, etc.)
			- MAC
			- Compression
			- SSL Version
			- Random number for symmetric key generation
		2. Server
			- RSA
			- AES
			- HMAC-SHA1
			- etc.
2. Server sends certificate
	- Serial number
	- Issuer (e.g. Verisign)
	- Valid dates
	- Public key
	- Etc.
3. Cliend sends details
	- Generate session key
	- Encrypt session key using server public key
	- key exchange
	- validate the server identity
	- decide cipher specifications
	- hand shake finished
4. Commence secure communication
	-	Update cipher spec.
	-	Handshake finished

Message integrity:
- MAC (message authentication code)
- Message confidentiality
	- selects encryption
How MAC works
- hash message, send hash with message
- compare your own hash of message with the hash you receive

Can SSL mitigate MITM attack? Yes, unless...
- untrustworthy certificate authority
- leaked shared private key
- client doesn't validate the certificate correctly
- client can be compromised

What type of attacks does SSL prevent/mitigate?
- mitigates attacks that try to exploit a lack of confidentiality and integrity
- e.g.
	- sniffing
	- hijacking connections
	- forge messages

What happens when SSL uses flawed cryptosystem?
- since SSL relies on cryptography, if the attacker can attack the cryptosystem then the confidentiality and integrity SSL provides goes out the window.