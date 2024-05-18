
- Within a Kubernetes cluster, every pod can reach every other pod 
	- This is accomplished by deploying a pod networking solution to the cluster
- A pod network is an internal virtual network that spans across all the nodes in the cluster to which all the pods connect to
- Through this network, they're all able to communicate with each other

#### About Kube Proxy

- Kube proxy is a process that runs on each node in the Kubernetes cluster - its job is to look for new services and every time a service is created, it creates the appropriate rules on each node to forward traffic to those services to the backend pod
