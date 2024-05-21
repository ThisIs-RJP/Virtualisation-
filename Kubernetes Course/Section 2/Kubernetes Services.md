
#### Kubernetes Services

- Enable communication between various components within and outside the application
	- Helps us connect applications together with other applications or users
- Suppose we have pods running various sections 
	- A group for serving front end loads to users
	- Another for running background processes
	- And a third to connect to an external data source
- It is Services that enable connectivity between these pods
- Services enable loose coupling between microservices in our application


#### How do external users access the web page?

- We want to be able to access a web server without having to SSH into the node and simply by accessing the IP of the Kubernetes node.
	- So we need something in the middle to help us match requests to the node from our laptops, through the node, to the pod running the web controller
- This is where Kubernetes Services comes in

#### About the Kubernetes Services

- Is an object
- One of the use cases is to listen to a port on the node and forward request on that port to a port on the pod running the web application
	- This is called NodePort service

#### Service Types

- Already discussed NodePort - where the service makes an internal port accessible on a port on the node
- ClusterIP - creates a virtual IP inside the cluster to enable communication between different services
	- Such as as set of front end servers to a set of backend servers
- LoadBalancer - provisions a load balancer for our application in supported cloud providers
	- In other words, it distributes oncoming traffic across multiple pods, services, or instances, to ensure reliability, availability and scalability

#### NodePort diagram

- Note: the whole box is the node
![[Pasted image 20240519223057.png]]