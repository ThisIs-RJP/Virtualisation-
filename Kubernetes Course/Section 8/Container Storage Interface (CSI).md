
#### Container Runtime Interface

- A standard that defines how an orchestration solution in Kubernetes would communicate with container runtimes like Dockers

#### Container Networking Interface

- Introduced to extend the support for different networking solutions

#### Container Storage Interface

Basically allows Kubernetes to connect to and use different types of storage (like cloud storage, local disks or network storage) without needing to know the details of how each storage system works 

- Developed to support multiple storage solutions
- You can now write your own drivers for your own storage to work with Kubernetes
- It defines a set of RPC's or remote procedure calls that will be called by the container orchestrator and these must be implemented by the storage drivers 
	- RPC = Remote Procedure Call, used to communicate between processes on different workstations

###### Example!

- CSI says that when a pod is created and requires a volume, the container orchestrator (in this case Kubernetes), should call the create volume RPC and pass a set of details such as the volume name
- The storage driver should implement this RPC and handle that request and provision a new volume on the storage array and return the results of the operation

###### Similarly...

The container orchestrator should call the delete volume RPC when a volume needs to be deleted and the storage driver should implement the code to decommission the volume from the array when that call has to be made