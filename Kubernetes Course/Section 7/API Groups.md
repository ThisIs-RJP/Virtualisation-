
The Kubernetes API is grouped into multiple such groups based on their purpose such as one for API's, one for health, one for metrics and logs etc...

**Version API** - for viewing the version of the cluster
**Metrics and Health API** - monitor the health of the cluster
**Logs** - for integrating third-party logging applications 


### API's focusing on the cluster's functionality

Categorised into 2 - the core group and the named group

###### Core

- Where all core functionality exists
	- Namespaces
	- Pods
	- Replication Controllers
	- Nodes
	- Secrets
	- Services
	- etc

###### Named

- More organised
- Has groups under it for
	- Apps
	- Extensions
	- Networking
	- Storage
	- Authentication
	- Authorisation
	- etc
- E.G, within apps is
	- Deployments
	- Replica sets
	- Stateful sets
- Within networking you have network policies
- Certificates you have these certificate signing requests
	
	![[Pasted image 20240610182422.png]]

- The one's at the top are the API groups, below them are the resources of these groups
- Each resource has their actions - things that you can do with these resources
	- List deployments, get info about deployments, update a deployment etc
	- These are called **verbs**
- 