
#### Introduction

- Scheduler takes into consideration the amount of resources required by a pod and identifies the best node to place the pod on
	- If nodes have no sufficient resources available, the scheduler avoids placing pods in those nodes and chooses others that do
	- If there are no sufficient resources, the scheduler hold back the scheduling and you will see the pod in a pending state with an **insufficient CPU** event

#### About the pods

- You can specify the amount of CPU and memory required for a pod when creating one 
	- This is known as a resource request
- When the scheduler gets a request to place this pod, it looks for a node that has this amount of resources available  
	- This ensures that the pod gets a guaranteed amount of resources available to it

#### About the nodes

- By default, a container has no limit to the resources it can consume on the node 
	- This means that it can go up and consume as much resources as it requires - this suffocates the native processes on the node or other container of resources
- You can limit how much resources the containers can consume
- However, this is not the case with memory meaning a container can use more memory resources than its limit
	- If a pod tries to consume more memory than its limit constantly, it'll be terminated (OOM)
- You need to make sure that all the pods have some requests set - it  is the only way a pod will have resources guaranteed

#### Behaviour Memory

- When a pod requests more memory that is being taken by another pod, the only way to get the memory back is to kill it

#### LimitRange

- Ensures that every pod created has some default set for limits
- You can do the same on pods however, the limits are only enforced when a pod is created - already existing pods are not affected

#### Resource Quota

- A way to restrict the total amount of resources that can be consumed by applications in a Kubernetes cluster
- Quotas are a namespace level object that can be created to set hard limits for requests and limits
	- e.g you can limit the total requested CPU and memory in the current namespace 