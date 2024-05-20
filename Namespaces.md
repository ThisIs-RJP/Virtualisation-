
#### Intro

- When we are creating our objects ( Services, Pods, Deployments), we were creating them in something called a namespace - specifically the default namespace, created automatically by Kubernetes when the cluster was first set up
- To isolate these pods and services are isolated from the user to prevent you from accidentally deleting/modifying these services, Kubernetes creates them under another name space created at cluster setup called kube-system
- The third namespace is called kube-public
	- This is where all resources that should be made available to all users are created
- If the environment is small, namespaces aren't important
- You can create your own namespaces as well
	- For example, if you wanted to use the same cluster for both dev and production environments but at the same time, isolate their resources, you can create a different namespace for each of them
		- This way, if you work in the dev environment, you don't accidentally modify the resources in production
- Each of these namespaces can have their own set of policies to define who can do what
	- You can also assign a quota of resources to each of these name spaces - this way each space is guaranteed a certain amount and doesn't use more than it should

#### Inside namespaces

- Resources within the namespace can simple refer to each other by their names 
- You can also access resources in another name space - to do this, you need to append the name of the name space to the name of the service
![[Pasted image 20240519231619.png]]

- Above is accessing resources in another namespace

#### Important commands

```kubectl get pods --namespace=kube-system```
- Listing pods in another name space