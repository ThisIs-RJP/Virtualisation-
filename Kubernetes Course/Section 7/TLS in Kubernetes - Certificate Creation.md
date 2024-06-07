
#### How to create a CA certificate

1. Create a private key using the OpenSSL command
2. Use the OpenSSL Request command with the key we just created to generate a cert signing request - this request is like a cert with all your details but without your signature
	- In other words it includes info about the cert you want to create - organisation names, the domain
3. We then use this cert signing request and an OpenSSL command to sign the certificate 
	- Since this is for the CA itself it is self signed by the CA using its own private key that it generated in the first step

#### How to create a client cert

1. Create a private key using the OpenSSL command
2. Use the OpenSSL Request command with the key we just created to generate a cert signing request
3. Using the private key and the CSR, you can now generate the CA certificate. The CA certificate will be used to sign other certificates.

#### How do you differentiate a user from another?

- The user account needs to be identified as an admin user and not just another basic user
- You can do that by adding the group details for the user in the cert
- Once it is signed we have our cert for the admin user with admin privileges

###### Note: we follow the same process to generate client privileges

#### What to do with these certs?

- You can use the certs instead of a username and password in a REST API call you make to the API server
- Other way is to move all of these parameters into a config file called kubeconfig. 
	- Within that, specify the API server endpoint details, the certs to use etc
- 