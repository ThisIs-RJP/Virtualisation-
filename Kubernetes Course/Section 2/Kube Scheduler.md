- Responsible for scheduling pods on nodes ONLY
	- Only responsible for deciding which pod goes on which node - doesn't actually place the pod on the nodes
		- The kubelet is who creates the pods on the ships
- You want to make sure that the container ends up on the right ship
	- To make sure that the ship has enough resources for that container
	- Also different ships go to different directions - you want to make sure that your container ends up in the right destination

#### Kube Scheduler criteria

- Scheduler decides which nodes the pods are placed on depending on certain criteria
	- You may have pods with different resource requirements 
	- You can have nodes in the cluster dedicated to certain applications
- So how does the scheduler know how to assign these pods?
- The scheduler looks at each pod and tries to find the best node for it
- A scheduler can determine which node to place the pod in by looking at the individual resources of each pod
	- The scheduler discards all the nodes that don't have sufficient resources and moves onto the ones that do
	- Once it has the nodes that meet the requirements of the pod, the scheduler than checks which node would have the *highest* remaining resources when the pod is placed onto that node
- 