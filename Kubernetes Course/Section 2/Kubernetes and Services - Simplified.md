
#### First off, what is a Service?

- A Kubernetes Service provides a stable, reliable way to route traffic to a set of pods. It is an way to expose an application running on a set of pods as a network service
	- In other words, it lets the users or applications to access other applications in the cluster

#### Now, we can go over some very important Services

##### NodePort
- A service that exposes an application running inside the cluster to users outside the cluster by allocating a static port on each Node's IP address - this is the NodePort
	- This allows the service to be accessed from outside the cluster
- Any traffic sent to any node at this port is forwarded to the service

###### How does this work?
- Kubernetes allocated a port from the NodePort range (30000-32767), and this port is open on all nodes in the cluster
	- External users can access this service ```<NodeIP>:<NodePort>```

##### ClusterIP

- When you create a service in Kubernetes without specifying the type, it defaults to "ClusterIP"
- The ClusterIP exposes the service on an internal IP address within the cluster
	- This means that the service is accessible only within the Kubernetes cluster and not from the outside
- Each service gets a name and an IP address assigned to it - this is the name that the other pods will use to access this service
- **Remember:** A ClusterIP is a type of Kubernetes Service that provides an internal IP address ONLY WITHIN the cluster, allowing services, pods and deployments to communicate with each other

#### How can a user access the application through the NodePort?

There are 2 ways a user can access an application through the NodePort

- The first method, is to use the Ingress resource
- The second method involves configuring the DNS to map the a domain name to the IP address of your Kubernetes nodes
	- Suppose you have a domain name ```myapp.example.com``` accessible at an IP ```10.0.0.1```
		- In our cluster, we have pods at a port ```8080``` and a node's IP address at port ```31000```
	- Generally, the user can access this application using ```http://10.0.0.1:31000```
	- But, using a DNS allows us to replace the IP address with the domain name
		- Which means the application can be accessible through
			- ```http://myapp.example.com:31000```