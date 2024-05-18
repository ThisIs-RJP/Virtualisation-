
- Kubelet is like the captain in the ship, responsible for everything happening on the ship
- Sole point of contact from the mastership
- Load/unload containers on the ship 
- Send back reports at regular intervals on the status of the ship and the containers


#### In the Kubernetes worker nodes...

- Registers the node with a Kubernetes cluster
- When it receives instructions to load a container or a pod on the node, it requests the container runtime engine to pull the required image and run an instance
- The kubelet then continues to monitor the state of the pod and containers in it and reports it back to the kube API server