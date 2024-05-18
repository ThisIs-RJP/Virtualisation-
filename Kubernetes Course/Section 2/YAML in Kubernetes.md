
- Kubernetes uses YAML files as inputs for the creation of objects such as pods, replicas, deployments, services etc
- A Kubernetes file always contains 4 top level fields
	1. the API version - version of the Kubernetes API we are using to create the object
	2. Kind - the type of object we are trying to create (pod, replica, deployment, service etc)
	3. Metadata - data about the object, like its name, labels etc. Values are in the form of a dictionary
	4. Spec
- These are also required fields


#### About metadata
- Inside metadata, it's best to label each file as there will be many pods (or there are *many* pods) and it will be difficult to group these pods once they're deployed
	- If they have a proper label, we can filter them
- You can only specify name/labels or anything else that Kubernetes expects to be under metadata - you cannot add any other property as you wish under this
	- However, under labels, you can have any kind of key, value pairs as you see fit

#### About spec

- The spec contains any additional information to Kubernetes pertaining to that object
- Spec is a dictionary, so add a property under it called containers
	- Containers is a list - this is because pods can have multiple containers in them
- The "-" right before the name indicates that this is the first item in the list