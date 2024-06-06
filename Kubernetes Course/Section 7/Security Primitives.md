

#### Introduction

- All access to the hosts (the hosts that form the cluster) must be secured - route access disabled, password based authentication disabled and only SSH key based authentication to be made available
	- Obviously if this is compromised, everything is compromised

#### About the kube-apiserver

- The kube-apiserver is the center of all operations within Kubernetes 
	- We interact with it through the kube control utility or by accessing the API directly
- This will be our first line of defense - controlling access to the API server itself 
- We need to make 2 decisions
	1. Who can access the cluster?
	2. What can they do?

#### Authentication 

- Who can access the API server is defined by the authentication mechanisms
- There are a few ways that you can authenticate to the API server
	- Starting with the user ID's and passwords stored in static files or tokens, certificates

#### Authentication - when they gain access to the cluster

- Authentication is implemented using role-based access controls where users are associated to groups with specific permissions
- Other authorisation modules like attribute-based access control, node authorisers, webhooks, etc

#### Communications within the Cluster

- All communications within the cluster between various components (e.g ETCD cluster, kube-controller-manager, API server) as well as those running on the worker nodes (e.g kubelet, kube-proxy) are secured using TLS encryption
	- TLS => <u>Transport Layer Security</u> is a cryptographic protocol designed to provide communications security over a computer network

#### Communication between applications within the cluster

- By default, pods can access other pods within the cluster
- You can restrict access between them using network policies