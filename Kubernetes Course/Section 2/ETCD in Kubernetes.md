
- Every information you see when you run the kube control get command is from the ETCD server
- Every change you make to your cluster are updated in the ETCD server
	- When it updates in the server, the change can be considered as complete
- There are 2 different types of Kubernetes deployments
	- One deployed from scratch
	- The other using the Qadium tool

#### From scratch

- If you setup your cluster from scratch, then you deploy ETCD by downloading the ETCD binaries yourself and installing the binaries and configuring ETCD as a service in your master node yourself
- There are many options passed into the service
	- But for now we'll only talk about the advertised client URL
- This is the address at which ETCD listens
	- Happens to be at the IP of the server and on port 2379
	- This is the URL that should be configured on the Kube API server

#### Setting up the cluster using Kubeadm 

- Kubeadm deploys the ETCD server for you as a pod in the kube system namespace
	- You can explore the ETCD control utility within this pod

#### Kubernetes data storage

- Kubernetes stores data in a very specific directory structure
	- The root directory is a registry and under that you have the various Kubernetes constructs, such as minions or nodes, pods, replica sets, deployments etc

#### More details

- In a high availability environment, you will have multiple master nodes in your cluster
- Then you will have multiple ETCD instances spread across the master nodes
- In that case, make sure that the ETCD instances know about each other by setting the right parameter in the ETCD service configuration
	- ETCD instances need to know about each other so they can distribute the workload and maintain the stability and integrity of the cluster
- The initial cluster option is where you must specify the different instances of the ETCD service