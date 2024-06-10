
#### What does authorisation mean?

What someone can do once they get access to something


##### Authorisation Mechanisms

- Node
- ABAC
- RBAC
- Webhook

#### About Node

- The kubelet accesses the API server to read information about services and points, nodes and pods
- These requests are handled by a special authoriser known as the **Node Authoriser**
	- In order words, their responsibility is to control and restrict the actions that nodes are allowed to perform within the cluster

#### ABAC - Attribute Based Authorisation

- Where you associate a user or a group of users with a set of permissions
	- E.G Dev-user can view, create and delete pods
- However, every time you want to make a change (add a user) you have to edit, and change the policy file manually and then restart the Kube API server

#### Role Based Access Controls

- Easier
- Instead you define a role (I.E developers) that have a set of permissions, then associate all the users for that role
	- Similarly we can create a role for security users with the right set of permissions for them

#### Webhook

- What if you wanted to manage the authorisation externally and not through built-in mechanisms
	-  For instance, Open Policy Agent is a third-party tool that helps with admission control and authorisation
	- You can have Kubernetes make an API call to the OPA with the information about the user and their access requirements and the OPA decides if the user should be permitted or not


###### There are 2 more nodes in addition to what we just covered

1. Always Allow
2. Always Deny

These names are self explanatory

#### Note

- The modes are set using the Authorisation Mode Option on the Kube API server
	- You may provide a comma separated list of multiple modes that you wish to use
- When a user sends a request, it is first handled by the Node Authoriser 
	- Only accepts node requests
- Whenever a module denies a request, it is forwarded to the next one in the chain
- When a module approves a request, no more checks are done and the user is granted permission 