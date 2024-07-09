
#### Notes

- Each node must have at least one interface
	- Each interface must have an address configured to it
- The host must have a unique host name set as well as a unique MAC address

#### About the ports

- Ports need to be opened as well
- The master node should accept connections on 6443 for the API server
- The worker nodes, kube control tool, external users and all other control plane components access the kube API server via this port
- The kubelets on the master and worker nodes listen on port 10250