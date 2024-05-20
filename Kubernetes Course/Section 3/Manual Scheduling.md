
#### What is a scheduler?

- A component that determines which node will run a particular container

#### What exactly does a scheduler do in the backend?

- Every pod has a field called NodeName - this is not set (by default)
- You don't specify this field, Kubernetes adds it automatically
- The Scheduler goes through all the pods and looks for those that do not have this property set - these are our candidates for scheduling
	- It then identifies the right node for the pod by running the scheduling algorithm
- Once identified, it schedules the pod on the node by setting the node name property to the name of the node by creating a binding object  

#### What if there is no scheduler to monitor and schedule notes?

- The pods continue to be in a pending state - but you can manually assign pods to notes yourself
- Easiest way to schedule a pod is to simply set the node name field to the name of the node in your pod specification file while creating the pod
	- Pod is then assigned to the specified node
- **Note:** you can only specify the node name at creation time

#### But what if the node is already created?
- Kubernetes won't allow you to modify the node name property of a pod, so another way to assign a node to an existing pod is to create a binding object and send a POST request to the pod's binding API
	- Binding - the process of associating a pod with a specific node
- In the binding object, you specify a target node with the name of the node, then send a POST request to the pod's binding API with the data set to the binding object in a JSON format