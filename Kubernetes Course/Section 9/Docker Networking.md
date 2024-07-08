
When Docker is installed, it creates an internal private network called Bridge by default

- Docker calls the network Bridge, but on the host its DockerO

Remember

- The bridge network is like an interface to the host but a switch to the namespaces or containers within the host

#### How does Docker attach the container to the bridge?

- It creates a cable, a virtual cable with 2 interfaces on each end

#### Every time a Docker creates a namespace...

- It creates a pair of interfaces, attaches one end to the container, and the other end to the bridge network

#### Accessing the containers outside

- When you run containers, tell Docker to map port 8080 on the Docker host to port 80 on the container
	- This means that any traffic forwarded to port 80 are forwarded to port 8080