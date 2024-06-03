
#### Scenario

- Suppose you have a cluster with a few nodes - what happens when one of these nodes go down?
- Of course the pods are no longer accessible
- Depending on how you deployed those pods, your users may be impacted
	- If such a pod only existed in that node that was taken down, users won't be able to access that pod - pods that exist in that node and others can still be accessed however

#### About Pod eviction timeout

-  If the node comes back online immediately then the kubelet process starts and the pods come back online
	- However if the node was down for more than 5 minutes then the pods are terminated from that node
	- If the pods were part of a replica set, then they are recreated on other nodes
- The time it waits for a pod to come back online is known as pod-eviction-timeout and is set on the controller manager with a default value of 5 minutes. 
	- So whenever a node goes offline, the master node waits for up to 5 minutes before considering the node dead 
	- If the node comes back online after the pod-eviction-timeout, it comes up blank without any pod scheduled on it 
		- If a pod from that node was part of a replica set, it is created on another node
		- If it wasn't it's just gone

#### How to maintain the nodes for upgrading 

- You can drain the node of all workloads so that the workloads are moved to other nodes in the cluster
- Node is cordoned - marked as unschedulable meaning no pods can be scheduled on this node
-  Now that the pods are safe on the other nodes, you can reboot the node
- When it comes back online it is  still unschedulable - you need to uncordon it
- Remember that the pods that were moved to the other nodes don't automatically fall back
	- If any of those pods were deleted or if new pods were created in the cluster, then they would be created on this node 