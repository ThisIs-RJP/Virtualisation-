
#### Note

Certificates with public keys have the `crt` or `.pem` extensions
Private keys have the `.key` extension or files can end with `-key` such as `server-key.pem` 
- Just remember that private keys usually have key in the name
- Ones without the key in them are public keys or certs

#### Within the cluster

- All interactions within the cluster need to be secure
	- An admin accessing the cluster must establish a secure TLS connection
- Communication within all components also need to be secure


###### Requirements?

- All services within the cluster use server certs
- All clients use client certs - to verify that they are who they say they are

#### Example - Kube API server

- Exposes an HTTPS service that other components, as well as clients, use to access the cluster
	- It is a server and requires a cert
- So we generate a cert and key pair
	- Call it `APIserver.cert` and `APIserver.key`

#### How about the clients

- The admin requires a cert and a key pair to authenticate to the kube-api server - the admin is a client
- The scheduler is also a client, one that's trying to access the kube-api server so it also needs to validate itself using a client TLS cert