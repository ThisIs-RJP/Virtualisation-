
## Using the analogy of ships

### Cluster Architecture

#### Intro
- Purpose of Kubernetes is to host your applications in the form of containers in an automated fashion
	- Easily to deploy between as many instances of that application and to easily enable communication between different services within your application
- 2 kinds of ships
	1. Cargo ships that do the actual work of carrying containers
	2. Control ships that are responsible for monitoring and managing the cargo ships
- A Kubernetes cluster consists of a set of nodes. These nodes may be:
	- Physical
	- Virtual
	- On premise
	- Or on cloud
		**Note:** Nodes are individual machines that make up a cluster. They work together to provide a platform for deploying, scaling and managing containerised applications
- These nodes host applications in the form of containers

#### Worker Nodes

- The cargo ships represent the <u>worker</u> nodes, but they need someone to load the containers onto them

#### Master Nodes

- This is done by the control ships, which represent the <u>master</u> nodes.
	- Master nodes:
		- plan everything
		- identify the right ships
		- store info about the ships
		- Monitor + Track the location of containers on the ships
		- Manage the whole process
		- etc...

- Master nodes achieve all of these using a set of components together known as the **control playing components
### Control Panel of the Master Node
#### ETCD

- Many containers are being loaded and unloaded from the ships on a daily basis
	- So you need to maintain information about the different ships, what container is on what ship and what time it was loaded
- All of these are stored in a highly available key value store, known as ETCD
	- ETCD is a database that stores information in a key value format

#### Kube-scheduler
- When ships arrive, you load containers on them using **cranes**. 
	- The cranes identify the containers that need to be placed on the ships. It identifies the right ship based on...
		- its size
		- its capacity
		- the number of containers already on that ship
		- other conditions such as the destination of the ship
		- the type of containers it is allowed to carry etc
- The cranes represent the <u>kube-scheduler</u>
	- A scheduler identifies the right node to place a container, based on:
		- the containers resource requirements
		- Worker nodes capacity
		- Any other policies or constraints, such as taints, tolerations or node affinity rules that are on them

#### Ship analogy for the different controllers in Kubernetes
- There are different offices in the dock that are assigned to special tasks or departments
	- The operations team takes care of ship handling, traffic control etc
		- They deal with issues related to damages, the route the different ships take etc
	- The cargo team takes care of the containers
		- When they are damaged, or destroyed they make sure that new containers are made available. 
	- Services office takes care of the IT and communications between different ships


#### Kubernetes controllers (Controller Manager)

- Node controller
	- Takes care of nodes
	- Responsible for 
		- Onboarding new nodes to the cluster
		- Handling situations where nodes become unavailable/destroyed
- Replication controller 
	- Ensures that the desired number of containers are running at all times in a replication group

#### Kube API

- The primary management component of Kubernetes
	- Responsible for orchestrating all operations within the cluster
		- Exposes the Kubernetes API which is used by external users to perform management operations on the cluster, as well as the various controllers to monitor the state of the cluster and to make changes when needed

#### More concepts

- Our applications are in the form of containers
- The different components that form the entire management system on the master node could be hosted in the form of containers
- We need a software that can run these containers - we need a container run time engine
	- Docker
- Docker needs to be installed on all the nodes in the cluster - including the master node, if you wish to host the controlling components as containers
	- Kubernetes also supports other engines
		-  ContainerD, Rocket

#### Kubelet, in the context of ships

- Every ship has a captain - kubelet
- Captains are responsible for managing all activities on these ships
	- Also responsible for liaising with the master ships, 
		- Starting with letting the master ship know that they're interested in joining the group
		- Receiving information about the containers to be loaded onto the ship 
		- Loading the appropriate containers as required
		- Sending reports back to the master about the status of this ship
		- The status of the containers of the ship

#### Kubelets explained

- A kubelet is an agent that runs on each node in a cluster
	- It listens for instructions from the Kube API server
		- Deploys or destroys containers on the nodes as required

- The Kube API server periodically fetches status reports from the kubelet to monitor the status of nodes and the containers in them

#### Kube Proxy Service

- Applications running on the worker nodes need to be able to communicate with each other
	- For example, you might have a web server running in one container on one of the nodes and a database server running on another container in another node
- Kube Proxy Services ensures that the necessary rules are in place on the worker nodes to allow the containers running on them to reach each other