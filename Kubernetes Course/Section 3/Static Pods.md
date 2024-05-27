
#### What are static pods

- Pods created by the kubelet on its own without the intervention from the API server
- A manifest file describes the pod configuration in YAML format
- The kubelet on the node must be configured to read the manifest from a specific directory
- You can view the pod using `docker ps` 
	- Remember `kubectl` only works if you have an API server!
- The kubelet can create a pod using the kube-apiserver and through pod definition files in the folder

#### API server is aware of the static pods created by the kubelet
 - If you run the `kubectl get pods` to get the pods in the nodes, the static pods will also be listed  
 - What you see from this is only a read-only mirror of the pod
	 - You can view the details about the pod, but you cannot edit or delete it like usual pods
	 - You can only delete them by modifying the files from the Nodes manifest folder 
#### Why use Static Pods?

- Static pods are not dependent on the control plane, so you can use static pods to deploy the control plane components itself as pods on the node 
	- Basically, to run essential system-level components directly on individual nodes without relying on the Kubernetes API server for their management - good for when the API server is unavailable

#### Remember
- The kube-scheduler has no effect on these pods