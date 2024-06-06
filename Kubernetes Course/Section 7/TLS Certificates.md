
#### What is a certificate

- A certificate is used to guarantee trust between 2 parties during a transaction
	- e.g when a user tries to access a web server, TLS certificates ensure that the communication between the user and the server is encrypted and the server is who it says it is

#### Asymmetric Encryption

- Instead of using a single key to encrypt and decrypt data, asymmetric encryption uses a pair of keys
	- A private
	- and public key
	- For now, we can call them private key and a public lock - a key and lock pair
		- A key that is private, (it's only with me) and a public lock that anybody can access
- The trick here is that if you encrypt or lock the data with your lock, you can only open it using an associated key
	- Your key must always be private
	- Because no matter what locks the public lock, only the private key and unlock it
- Just place your public key (lock) to all the necessary servers

###### Note

- You can secure as many servers as you want by creating multiple public locks and use the same private key
- Other users can access them too using their own key pairs

#### Scenario

- When a user first accesses the web server using HTTPS, he gets a key (a public key) from the server
	- Suppose the hacker intercepts and gets a hold of the public key
- The user's browser then encrypts the public key then sends it to the server
	- The hacker also gets this
- The server then uses the private key to decrypt the message and retrieve the symmetry key from it
	- The hacker does not have a private key and can't do anything with the key that they have
- The symmetry key is now safely available only to the user and the server and can now encrypt and send data to each other

#### Scenario 2

- But what if the hacker makes a website that looks identical to the website your are accessing using a key pair too?
	- That the keys even send a certificate with them
- How do you determine if the certificate is legit?
	- With certificates, if you generated one then you have to sign it - anybody looking at the certificate will know that it is not a safe certificate because you generated (signed) it. This is called a self signed certificate
	- If you look at the hackers certificate, you will know that it is not the bank
- All browsers checks the certificates that it receives and and validates if it is safe or not - if it looks unsafe it will warn you

#### How do you create a legitimate certificate?

- Certificate Authorities - organisations that will sign and validate certificates for you

###### How does it work?

- You generate a certificate signing a request using the key you generated earlier - this creates a file which is the certificate signing request that should be sent to the CA for signing
	- Once it checks out, they sign it and send it back to you
	- If a hacker tried to do this they would fail the validation phase and his certificate will be rejected by the CA. His server won't have a valid certificate

#### But how would a browser know that the certificate was not signed by a false CA?

- The CA's themselves have a set of public and private keys
- The CA's use their private keys to sign certificates and the public keys are all built into the browsers


#### Summary

- Server uses a key pair to secure HTTPS traffic
- For this, they need to send a cert signing request to a CA
- The CA uses their private keys to sign the CSR
	- All users have access to the CSR public key
- The signed cert is sent back to the server - server configures the application with the cert
- When a user tries to access the server, the server sends the cert with the public key
- Users browser reads the cert and uses the CA's public key to validate and retrieve the server's public key - it then generates a symmetric key using server's public key  which is encrypted and uses this to communicate with the server and sends this back to the server
- The server uses its private key to decrypt and retrieve the symmetric key


#### But how does the server know that the user is who they say they are?

- The server can request a cert from the client
- Client must generate a pair of keys and a signed cert from a CA and sends it to the server to verify that they are who they say they are

#### You must be careful on how you encrypt your keys

- If you encrypt with your private key, then anybody with your public key will be able to decrypt and read your message