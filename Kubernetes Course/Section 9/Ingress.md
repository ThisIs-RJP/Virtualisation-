
#### What is Ingress in Kubernetes

- An object that allows access to Kubernetes services from outside the Kubernetes cluster
	- I.E Ingress helps your users access the application using a single externally accessible URL that you can configure to route to different services within your cluster based on the URL path
	- You can configure access by creating a collection of rules that define which inbound **connections** reach which services
	- Helps implement SSL security as well
- Think of Ingress as a layer seven load balancer built in to the Kubernetes cluster that can be configured using native Kubernetes primitives just like any other object in Kubernetes
	- But you still have to expose it to make it accessible outside the cluster
	- This means that you have to either publish it as a NodePort or with a cloud native load balancer
		- This is just a one time configuration
- You must have an Ingress controller to satisfy an Ingress - AWS, Azure, GCP

#### Key Points

- Ingress is an API object that manages external access to the services in a cluster, typically HTTP - it means you can use Ingress to make your service accessible from the outside
- Ingress is not a Service type - it acts as the entry point for the cluster
- Ingress helps expose multiple services under the same IP address, using the same load balancers