
#### Is it mandatory for all of the control plane components to be the same version?

No the components can be at different release versions

But...
- The primary component in the control plane is the kube-apiserver - this is the component that all other components talk to
	- Therefore the other components should not be at a version higher than the kube-apiserver
- The controller-manager and scheduler can be at one version lower 
- The kubelet and kube-proxy components can be at 2 versions lower 

###### However

- The kubectl utility could be a version higher, a version lower or the same version as the API server

#### Note

- Kubernetes supports only up to the recent 3 minor versions 
- To upgrade (E.G from 1.10 to 1.13), you have to upgrade one minor version at a time
	- This is for stability and control and risk management


#### Upgrading

- The upgrade process depends on how your clusters are set up 
	- If your cluster is a managed Kubernetes cluster deployed on a cloud service provider, the service lets you upgrade your cluster easily with a few clicks 
- If you deployed your cluster from scratch, then you manually upgrade the different component of the cluster yourself 

#### Upgrading Steps

1. Upgrade your master nodes
	- While the master is being upgraded, the control plane components go down briefly
2. Upgrade the worker nodes

 ###### Note 

- The master going down does not mean your worker nodes and applications on the cluster are impacted
	- All workloads hosted on the worker nodes continue to serve users as normal 
- Since the master is down, all management functions are down
	- E.G you cannot access the cluster using `kubectl` or other Kubernetes API 
	- You cannot deploy new applications or delete/modify existing ones
	- The controller-managers don't function either - if a pod fails a new pod won't be automatically created
- But as long as the nodes and the pods are up, your applications should be up and the users will not be impacted


#### Upgrading the worker nodes

- To upgrade the worker nodes, you can upgrade all of them at once
	- But the pods will be down and unaccessible
	- Once the upgrade is complete, the nodes are back up and the new pods are scheduled and users can access it again 
- The second strategy is upgrading the nodes one at a time
	- Upgrade the first node where the workloads are moved to the 2nd and 3rd node, so that users can be served from there
	- Once that node is finished, move to the next and upgrade that - workloads move to other nodes again
- The third strategy would be to add new nodes to the cluster - nodes with newer software versions
	- Nodes with newer software versions can be added to the cluster, move the workload over to the new node and remove the old node


#### About `kubeadm`

- `kubeadm upgrade plan` gives you a lot of information about the current cluster version
	- Lists all the control plane components and their versions and what version they can be upgraded to
	- Also tells you that after you upgrade the control plane components that you must manually upgrade the kubelet versions on each node 

###### Note

- `kubeadm` does not install or upgrade kubelets
- If you want to upgrade to a version the `kubeadm` must be the same as that version 

#### Steps when upgrading

###### Upgrading the kubelets

###### Upgrading the kubelet on the master nodes

###### Upgrading the worker nodes

- `kubectl drain` safely terminates all the pods from a node and reschedules them on the other nodes
- It also cordons the node - marks it unschedulable, this way no other pods are scheduled on it

###### Upgrade the `kubeadm` and kubelet packages on the worker nodes 
- as we did on the master node
###### Uncordon/Unmark the pods that were cordoned 

- So that they can be schedulable again
- Remember that the nodes don't come back - only when the are deleted from the other nodes will they be added to this node again