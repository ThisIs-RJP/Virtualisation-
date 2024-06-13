
A service account is a specialised account created for applications running within a Kubernetes cluster, allowing them to interact with the API.
Some key features include
- Allowing pods to perform actions and access the Kubernetes API
- Manage and restrict what a pod can do - enhancing security


#### Scenario 1

- Suppose we have a simple application that retrieves the lists of pods on a Kubernetes cluster
	- We can do this by sending a request to the Kubernetes API server and display it on the web page
- But in order to do any of these, the application needs to query the Kubernetes API and has to be authenticated
- For that we use a service account

#### Note

- When a service account is created, it automatically creates a token - which is stored as a secret object
	- A token created from a service account is what it uses to authenticate to the Kubernetes API
- You can create a service account, assign the right permissions using role-based access control mechanisms and export your service account tokens
- You cannot edit the service account of an existing pod - you must delete and recreate the pod
- You can in a deployment however - any changes to the deployment will automatically trigger a new rollout

#### What if the third-party application is hosted on the Kubernetes cluster itself?

- The process of exporting the service account token and configuring the third-party application to use it can be made simple by mounting the secret onto the pod hosting the application
- 