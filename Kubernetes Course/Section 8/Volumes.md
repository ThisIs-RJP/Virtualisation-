
#### Docker Containers

- Transient in nature - only meant to last for a short period of time
	- They are called upon when required to process data and destroyed once finished
- To keep data processed by the container, we attach a volume to the containers when they are created - the data is now processed and placed into this volume 

#### Host Path Option

However, the host path option is not recommended for use in a multi node cluster because the pods would use the slash directory
- Nodes in the cluster will save the data in a `/data` directory on all nodes but since they are different servers, they save different data