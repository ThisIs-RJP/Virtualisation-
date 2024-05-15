
#### Container Runtime Interface
- Allowed any vendor to work as a container runtime for Kubernetes as long as they adhere to the OCI standards

#### OCI
- OCI stands for Open Container Initiative
	- Consists of an imagespec
		- The specifications on how an image should be build
	- and a runtimespec
		- How any container runtime should be developed
- However, Docker wasn't built to support the OCI standard...
	- Kubernetes introduced dockershim to continue the support for Docker

#### About Docker

- Docker consists of multiple tools that are put together
	-  Docker consists of multiple tools that are put together
		- Docker CLI and Docker API help build images 
	- There was support for volumes, auths, security, and finally the container runtime called runC and the daemon that managed runC that was called Containerd
- Containerd is CRI compatible and can work directly with Kubernetes as all other runtimes
	- Containerd can be used as a runtime on its own separate from Docker
	- As a result, Kubernetes continued to maintain support for Docker engine directly

#### Containerd

- Separate project on its own now, and a member of CNCF with the graduated status
	- CNCF => Cloud Native Computing Foundation - an organisation that oversees many open-source projects related to cloud-native computing.
- If you don't need Docker's other features, you can use Containerd

#### Containerd command ```ctr```

- Command line tool
- Tool is solely made for debugging Containerd - not every user friendly, not to be used for running or managing containers
	- Only supports a limited set of features
- ```ctr``` command can be used to perform basic container related activities
	- e.g pull images
- Example: Pull redis image
	-  ```ctr images pull docker.io/libary/redis:alpine```
- Example: Run a container
	- ```ctr run docker.io/libary/redis:alpine redis```

#### Containerd command ```nerdctl```

- Command line tool
- Supports most options that Docker supports
- Can give us access to the newest features implemented into Containerd
	- We can work with encrypted container images
	- Supports:
		- Lazy pulling of images
			- Lazy Pulling is a strategy in container orchestration where container images are not pulled from a registry until they are actually needed, optimising resource usage and speeding up deployment times
		- P2P (peer to peer) image distribution
			- A network model where devices can communicate directly with each other without relying on a central server
		- Image signing
		- Verifying
	- ```nerdctl``` works almost like Docker, where instead of using ```docker``` you use ```nerdctl```
	- e.g Run a command
		- In Docker
			- ```docker run --name redis redis:alpha```
		- Using ```nerdctl```
			- ```nerdctl run --name redis redis:alpha```

#### Containerd command ```crictl``` aka *cri control*

- ```crictl``` is a command line utility that is used to interact with the CRI compatible container runtime
- This tool is developed and maintained by the Kubernetes community, unlike ```ctr``` and ```nerdctl``` tools that are developed and maintained by the Containerd community specifically for Containerd
	- As a result, it must be installed separately 
- Used to inspect and debug container runtime, not ideally used to create containers
	- Only used for special debugging
- Kind of works with the kubelet that is responsible for ensuring that the specific number of containers or pods are available at a node at a time
	- If you try create anything, the kubelet will delete it because the containers were created outside of its knowledge
- Now for some code
- Example: pull images
	- ```crictl pull busybox```
- Example: list existing images
	- ```crictl images```
- Example: list containers
	- ```crictl ps -a```
- Example: run command inside a container
	- ```crictl exec -i -t <containerID> <commandToRun>``` , sample command to run can be ```ls``` 
- Example: View logs
	- ```crictl logs <containerID>```
-  ```crictl``` used a lot to troubleshoot containers and view logs

![[Pasted image 20240515183556.png]]