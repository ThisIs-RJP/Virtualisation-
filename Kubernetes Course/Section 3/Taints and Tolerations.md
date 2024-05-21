#### What are Taints and Tolerations

- Taints and Tolerations are used to set restrictions on what pods can be scheduled on a node 


#### Scenario

- Suppose we have a set of pods - A, B, C, D
- When the pods are created, the Kubernetes scheduler tries to place these pods on the available worker nodes
- As of now, there are no restrictions or limitations and as such, the scheduler places the pods across all of the nodes to balance them out equally
- Let's assume that we have dedicated resources on node one for a particular use case or application
	- So, we would like only those pods that belong on this application to be placed on node one 
- First, we would prevent all pods from being placed on the node by placing a taint on the node - let's call this pod blue
- By default, pods have no tolerations, which means unless specified otherwise, none of the pods can tolerate the taint
	- This means that none of the pods can be placed in node one, as none of them tolerate the taint blue
- This only solves half of our requirement
	- None of the unwanted pods will be placed on this node
- The next half is to enable certain pods to be placed on this node
- For this we need to specify which pods are tolerant to this taint
	- In our case, we only want pod D to be placed into this node
- So we add a toleration to pod D - is now tolerant to blue and can now go into node one

	Now, let's put everything together
1. The scheduler tries to place pod A on node 1 - thrown off because of the taint, so it goes into node 2
2. The scheduler tries to place pod B into node one - thrown off because of the taint, goes for node 2 but thrown away again because of the limit, so it goes into node 3
3. Scheduler tries to place pod C into node 1 - thrown off because of taint, so it goes into node 2 
4. Finally, scheduler tries to place pod D into node 1 - goes through because it is tolerant to node one

![[Pasted image 20240520121355.png]]


#### The 3 taint effects

##### NoSchedule
- Pods will not be scheduled on the node

#### PreferNoSchedule

- System will try to avoid placing a pod on the node, but that is not guaranteed

#### NoExecute

- New pods will not be scheduled on the node and existing pods (if any) will be evicted if they do not tolerate the taint

#### Example code
```kubectl taint nodes node1 app=blue:NoSchedule```


#### Scenario 2

- *Using the same setup from the previous example (just without the taints or tolerations)*
![[Pasted image 20240520122442.png]]

 - While tainting the node, suppose we add a taint effect to NoExecute
 - The node takes effect (pod D has toleration)
	 - Pod C is evicted from the node - it was killed

#### Remember!
- Taints and tolerations are only meant to restrict nodes from accepting certain pods
	- It doesn't guarantee that a pod will be placed into a certain node
- Taints and tolerations tells the NODE to only accept pods with certain tolerations

#### Taints and Tolerations on the Master Node

- A taint is set on the master node automatically
	- Prevents any pods to be scheduled on this node
- Best practice is to not deploy application workloads on a master server
- You can check the taint of the master node using
	```kubectl describe node kubemaster | grep Taint```