
#### Scenario

- Suppose you have a 3 node cluster, 2 are smaller nodes with lower hardware resources, 1 is a larger node configured with higher resources
- You have different kids of workloads running in your cluster
- You would like to dedicate the data processing workloads that require higher horsepower to the larger node
	- it is the only not that will not run out of resources in case the job demands more resources
- However, in the current default setup, any pod can go to any node
	- Pod C, the bigger pod, goes into one of the 2 smaller nodes - we do not want this

#### Solution?

- Set a limitation on the pods so that they only run on particular nodes
- There are two ways to do this
1. Using Node Selectors
	- Simple, easier method
	- Using a ```pod-definition.yml```, we just specify a new property called ```nodeSelector```, and specify the size as large
	- The key value pair of ```size: Large``` are actually labels to match and identify the right node to place the pods on
- When we create the pod, the pod gets added into Node 1
