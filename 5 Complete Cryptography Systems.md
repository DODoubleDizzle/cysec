# 1 Digital Signatures

# 2 Digital Certificates 
A digital certificate serves as a mechanism to verify the ownership of a public key. It involves a trusted third party, typically managed through a Public Key Infrastructure (PKI). The process begins with the generation of a private and public key pair by the entity desiring the certificate (e.g., a server). This entity then creates a Certificate Signing Request (CSR), which is essentially an unverified certificate. The CSR is sent to a Certification Authority (CA), which performs identity checks and, upon verification, signs the certificate with its private key, thereby endorsing the association between the public key and the identity of its owner. This signed certificate can then be used to prove the entity's identity to others​​.

### 2.1.1 TLS connection
The most widespread use of digital certificates is in the setup of secure connections between clients (e.g., web browsers) and servers using protocols like TLS (Transport Layer Security). When a client attempts to connect to a secure server (e.g., a website using HTTPS), the server presents its digital certificate to the client. This certificate contains the server's public key and is signed by a trusted Certification Authority (CA). The client verifies the certificate's authenticity by checking the CA's signature, ensuring the server is indeed who it claims to be, thus preventing man-in-the-middle attacks.

### 2.1.2 Encryption
Once the digital certificate is verified and a secure connection is established, the client and server can exchange information securely. The client may encrypt a session key using the server's public key (from the digital certificate). Only the server, with its corresponding private key, can decrypt this session key. This session key is then used to encrypt and decrypt the data exchanged during the session, ensuring confidentiality.

### 2.1.3 Authentication
Digital certificates authenticate the identity of entities on a network. For instance, when you visit a website, the digital certificate helps verify that the server you're connecting to is indeed the correct server for that website, not an imposter. This is crucial for preventing phishing attacks.

### 2.1.4 Digital Signatures
Digital certificates can also be used for creating digital signatures. An entity (like an individual or organization) can sign a document or a piece of data using their private key. The signature can be verified by others using the entity's public key provided in their digital certificate. This proves the integrity of the data and the identity of the signer.

