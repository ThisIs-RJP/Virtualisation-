

#### Scenario

Suppose you were new in a team and you were asked to perform a health check

- Start by identifying the certs used in the system
- We need to get the paths, the names configured on them (alternate names too), the organisation that the certs belong to, the issue of the cert and the expiration of the cert

#### How do we do this?

- Start by looking at the certs being used - look for the Kube API server definition file
	- The command used to start the API server has info about all the certs it uses
	- Identify the certs used 
- Next, take each cert and look inside it to find more details
	- Run the `openssl x509` and provide the cert as input to decode it and see the details