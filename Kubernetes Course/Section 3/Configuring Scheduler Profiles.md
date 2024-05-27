
- When pods are created, they end up in a scheduling queue
- Pods are sorted based on the priority defined on the pods
- This is how pods with higher priority get to the beginning of the queue to be scheduled first
- Pod enters **filter phase**
#### Filter Phase

- This is where nodes that cannot run the pod are filtered out
	- Nodes that do not fit the requirements of the pod are filtered out 
- Pod then enters **scoring phase**

####  Scoring Phase

- Scheduler associates a score to each node based on the free space that it will have if the pod were to be placed in that node
	- The node with the most resources over the others in relation to their resources after a pod were to be placed there will have a higher score
- Pod then enters the **binding phase**

#### Binding Phase

- This is where the pod is finally bound to a node with the highest score

## To achieve all of these operations
### Certain <u>plugins</u> are used

1. Scheduling Queue - PrioritySort
2.  Filtering - NodeResourcesFit, NodeName 
	- NodeName - If a pod has a mentioned node name, it filters out the nodes that do not match this name
3. Scoring - NodeResourcesFit, ImageLocality
	- Associates a high score to the nodes that already has the container image used by the pods among the different nodes
4. Binding - DefaultBinder


#### Kubernetes lets us customise what plugins go where and for us to write our own plugin

- This is achievable using extension points
	- Extension points are where a plugin can be plugged into 