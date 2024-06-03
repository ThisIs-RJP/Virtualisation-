
When you have multiple pod definition files, it becomes difficult to manage the environment data stored within the query's files
- Environment data - config settings and parameters that are passed to the applications running inside containers within pods
We can take this information out of the pod definition file and manage it centrally using configuration maps


#### About ConfigMaps

- ConfigMaps are used to pass configuration data in the form of key value pairs in Kubernetes 
	- When a pod is created, inject the config map into the pod so the key value pairs are available
		- These key value pairs are available as environmental variables for the application hosted inside the container in the pod

There are 2 phases involved in configuring config maps

1. Create config map
2. Inject them into the pod