
#### Networking Model

- Kubernetes expects every pod to get its own IP address
	- And that every other pod should be able to reach every other pod within the same node using that IP address
	- And that every pod should be able to reach every other pod on other nodes as well

![[Pasted image 20240709224318.png]]

### How to connect 2 pods together from different nodes

- Add a route to node one's routing table to route traffic to `10.244.2.2` where the second node's IP at `192.168.1.112` 
	- Once the route is added, the blue pod can access across


#### But how about the better solution?

- Configure the routes to a router if you have one in the network and point all hosts to use that as the default gateway
- This way, you can easily manage routes to all networks in the routing table on the router

#### How do we run a script automatically when a pod is created?

- We run a lot of scripts manually, we don't want to do this for larger environments
- This is where CNI comes in
	- So we need to modify the script to meet CNI standards
- The container runtime on each node is responsible for creating containers.
- Whenever a container is created, the container runtime looks at the CNI configuration passed as a command line argument when it was run