
#### About Daemon Sets

- Kind of like ReplicaSets - as in they help you deploy multiple instances of pods
	- But it only runs one copy of your pod on each node in the cluster
- Whenever a new node is added to the cluster, a replica of the pod is automatically added to that node
	- When a node is removed, the pod is automatically removed
- DaemonSet ensures that one copy of the pod is always present in all nodes in the cluster
- DaemonSets work on the entire cluster

#### Use cases for a DaemonSet

- Suppose you would like to deploy a monitoring agent or log collector on each of your nodes in the cluster so you can monitor your cluster better
	- DaemonSet is perfect for that - deploys your monitoring agent in the form of a pod in all nodes in your cluster
-  No need to worry about adding or removing monitoring agents from these nodes

#### How does a DaemonSet work

- We can set the node name property on the pod to bypass the scheduler and get the pod placed on a node directly
	- This is one approach
- DaemonSets however uses the default scheduler and node affinity rules to schedule pods on nodes