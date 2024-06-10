
#### What is the CA

- A pair of key and cert files we have generated
	- Whoever gains access to these pair of files can sign any cert for the Kubernetes environment - they can generate as many users as they want
- So these files definitely need to be protected - we can store them on a CA server

#### About the CA server

- The cert key file is safely stored in this server and only on this server
- Every time you want to sign a cert, you can only do so by logging into this server

###### Note that you master node can also be CA server as that the certs are also placed on the master node

#### But all of this is manual - what happens if the amount of users grows?

###### Answer: The Kubernetes built-in cert API

- An admin can create an object called **CertificateSigningRequest**
- Once created, all cert signing requests can be seen by admins of the cluster
	- This request can be reviewed and approved easily using `kubectl` commands

#### How it works

- A user creates a key then generates a cert signing request using the key with their name on it and send it to the admin
- The admin takes the key and creates a CertificateSigningRequest object
	- You can create one using a `definition.yaml` file just like any other Kubernetes object
	- Under the `spec` at the request field, you can specify the cert signing request sent by the user
		- Must be encoded using the Base64 
- Once this object is created, all admins can see all the cert signing requests 
	- They can approve the requests using the `kubectl` commands
- Kubernetes signs the cert using the CA key pairs and generates a cert for the user
- This cert can then be extracted and sent back to the user

#### Remember!

All cert related operations are carried out by the controller manager
- It has controllers called CSR-Approving and CSR-Signing - they are responsible for carrying out these specific tasks
- If anybody has to sign these certs they need to use the CA servers root cert and private key