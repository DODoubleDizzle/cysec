# 1 TLS Architecture
## 1.1 TLS Connection
- Is a transport that provides a suitable type of service 
- Such connections are peer-to-peer relationships
- Connections are temporary, or non-persistent
## 1.2 TLS Session
- Is an association between a client and a server created by the Handshake Protocol 
- Defines a set of cryptographic security parameters which can be shared among multiple connections
- Sessions are used to avoid the expensive negotiation of new security parameters for each connection

## 1.3 TLS History
- 1994 SSL 1.0 (unpublished) 
- 1995 SSL 2.0 
- 1996 SSL 3.0 
- 1999 TLS 1.0 – RFC 2246, roughly identical to SSL 3.0 
- 2006 TLS 1.1 – RFC 4346
	- Security fixes and removed some methods of encryption 
- 2008 TLS 1.2 – RFC 5246
	- Authenticated encryption added
	- hashing function improved
	- many TLS extensions added 
- 2018 TLS 1.3 – RFC 8446 
	- redesign for performance
	- old ciphers removed
	- only available with AEAD (authenticated encryption)



# 2 TLS Handshake
## 2.1 Phase 1

### 2.1.1 Client hello
Client sends Hello, this message includes 
- the clients TLS version number
- a list of supported cipher suites (algorithms for encryption, key exchange, and message authentication)
- a list of supported extensions
- a randomly generated value that will be used in subsequent steps to generate encryption keys.

### 2.1.2 Server hello
In response to the client hello. 
- servers chosen protocol version (usually the highest version supported by both the client and the server)
- the cipher suite selected from the list provided by the client
- the session ID for session resumption (if applicable)
- another randomly generated value.

## 2.2 Phase 2
### 2.2.1 Server certificate
Following the [[#2 TLS Handshake#2.1 Phase 1#2.1.2 Server hello|Server hello]], the server sends its digital certificate to the client which allows the client to verify the servers identity. The certificate typically includes servers public key, which the client will use for encrypting messages intended for the server.

### 2.2.2 Server key exchange (Optional)
This optional message is sent by the server only if the selected cipher suite requires additional information for the key exchange process. 

> [!info] Example
> 
For example, in Diffie-Hellman key exchange, this message would contain the parameters necessary for the client to generate a pre-master secret.

### 2.2.3 Server hello done
This message indicates that the server has finished sending messages to support the key exchange and is now waiting for the client's response. After this message, the server will expect a response from the client to proceed with the handshake.
## 2.3 Phase 3

### 2.3.1 Client key exchange
The content of this message depends on the key exchange method agreed upon during Phase 1. 

> [!Info] Example
> For RSA key exchange, this message contains a pre-master secret encrypted with the server's public key. For Diffie-Hellman key exchange (either fixed or ephemeral), it contains the client's public parameters, which the server will use to generate the same pre-master secret.

### 2.3.2 Client certificate verify
If client authentication is required (and the client has sent a certificate to the server), the client must send a "Certificate Verify" message. This message provides cryptographic proof that the client has the private key corresponding to the public key in the certificate it presented. This is accomplished by signing a hash of all the messages exchanged so far and sending this signature to the server.

### 2.3.3 Client change cipher spec
This is technically not part of the TLS handshake protocol itself but rather a signal from the client to the server indicating that subsequent messages from the client will be encrypted using the session keys derived from the pre-master secret.
## 2.4 Phase 4
### 2.4.1 Client handshake finished
To verify that the handshake was successful and not tampered with, the client calculates verification data that the server will agree on, and encrypts it with the client handshake key. The verification data is built from a hash of all handshake messages.

### 2.4.2 Server change cipher spec
This is technically not part of the TLS handshake protocol itself but rather a signal from the server to the client indicating that subsequent messages from the server will be encrypted using the session keys derived from the pre-master secret.

### 2.4.3 Server handshake finished
To verify that the handshake was successful and not tampered with, the server calculates verification data that client will agree on. The verification data is built from a hash of all handshake messages.

### 2.4.4 Client  & Server Application data 
Now they can exchange application data

# 3 Alert Protocol
Conveys TLS alerts to peer entity, they are compressed and encrypted
An alert message has two bytes:
- The first byte has the value warning(1) or fatal(2)
- the second byte has a code that indicates the specific alert

> [!Warning] Important
> If the alert level is fatal, TLS immediately terminates the connection.

# 4 Heartbeat protocol
A periodic signal generated by hardware or software to indicate normal operation or to synchronize other parts of a system 
-  Typically used to monitor the availability of a protocol entity 
- Defined in 2012 in RFC 6250
- Use is established during Phase 1 of the Handshake Protocol 
- Each peer indicates whether it supports heartbeats 
- Serves two purposes: 
	- Assures the sender that the recipient is still alive
	- Generates activity across the connection during idle periods
## 4.1 Heartbleed
When a heartbeat request is sent, it includes a payload (the heartbeat message) and the payload's length. The server then copies the message into a response and sends it back to ensure the connection is alive. The vulnerability was that OpenSSL did not properly validate the length of the heartbeat request. An attacker could send a maliciously crafted heartbeat request that claimed the payload was longer than it actually was. The server would then respond with a heartbeat response that contained not only the payload but also whatever additional data was in memory up to the length specified by the attacker. This could include sensitive data such as private keys, usernames, and passwords.

# 5 TLS 1.3
## 5.1 Improvements
### 5.1.1 Cleanup
- Removed legacy and broken cryptography (3DES, AES-CBC, Arbitrary Diffie-Hellman groups, Export ciphers, DES, MD5, RC4, RSA key transport, SHA-1)
- Remove broken features: compression and renegotiation
- Remove static RSA/DH (breaks enterprise proxies doing passive inspection)
### 5.1.2 Performance
- TLS 1.2 needs 2 round trips before client can send data 
- TLS 1.3 needs only 1 or:
	- When users return to a TLS-secured website that they previously visited, it will load even faster because their browser will "remember" that the site is trustworthy. Therefore, it can send data to the server right away. This feature is known as "zero round trip time resumption," or 0-RTT
### 5.1.3 Privacy
Encrypt more of the protocol, almost all handshake messages not only application data like before
### 5.1.4 Compatibility
It is also backwards compatible

