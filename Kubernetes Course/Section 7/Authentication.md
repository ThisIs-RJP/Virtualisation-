
#### Introduction

- The Kubernetes cluster consists of multiple nodes, physical or virtual and various components that work together
	- We have users like admins that access the cluster to perform administrative tasks
	- The developers to test and deploy applications
	- End users who access the applications deployed on the cluster
	- And third party applications accessing the cluster for integration purposes

#### The different users that may be accessing the cluster

- The security of end users accessing the application deployed the cluster is managed by the applications themselves internally
- Kubernetes does not manage user accounts natively - it relies on an external source like a file with user details or certificates or a third party service like LDAP to manage these users
	- LDAP => Lightweight directory access protocol (LDAP) is a protocol that helps users find data about organisations, persons, and more
		-  2 main goals: to store data in the LDAP directory and authenticate users to access the directory

#### Kube-apiserver and authentication

 - All user access is managed by the API server
 - The Kube API server authenticates the request before processing it

###### But how does it authenticate?

- A list of username and passwords in a static password file
	- Or usernames and tokens in a static token file
- Or you can authenticate with certificates
- Third party authentication protocols like LDAP


#### Static Password

- Create a list of users and passwords in a CSV file and use that as the source for user information
- File has 3 columns
	- Password
	- Username
	- User ID
- We then pass the file name to the Kube API server
- Restart the API server afterwards
- You can also have a 4th column with the group details to assign users to specific groups

#### Static Token File

- Instead of password, you specify a token



### However, these are still not secure enough...