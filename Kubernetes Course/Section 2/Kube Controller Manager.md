

#### About the Kube Controller Manager

- Manages various controllers in Kubernetes
	- A controller is like an office/department within the mastership that have their own set of responsibilities
		- e.g an office for the ships would be responsible for monitoring and taking necessary actions about the ships, whenever a new ship arrives or when a ship leaves/gets destroyed
		- Another office could manage the containers on the ships
- In Kubernetes terms, these controllers are processes that continuously monitor the state of various components within the system to bring the system to its desired state

####  Node Controller

- Responsible for monitoring the status of the nodes and taking necessary actions to keep the applications running
	- It does it through the Kube API server
		- This controller checks the status's of the nodes every 5 seconds
		- If it doesn't get a heartbeat from that node, it waits 40 seconds before marking it as unreachable
		- After a node is marked unreachable, it gives it 5 mins to come back up.
			- If it fails again it removes the POD's assigned to that node and provisions them on the healthy ones if the POD's are part of a replica set

#### Replication Controller

- Responsible for monitoring the status of replica sets and ensuring that the desired number of POD's are available at all times within that set
	- If a POD dies, it creates another one

#### Kubernetes Control Manager

- Controllers packaged into a single process - essentially the brain behind a lot of the things in Kubernetes
	- When you install the Kubernetes Control Manager, the different controllers are installed as well