
- Suppose we have a web application that consist of
	- Front end pods
	- back-end pods
	- a database
- How do we connect all of these together?
- Each pod will have an IP address
	- These are not static, new pods are created all the time so these will not be the same all the time
- What if one of the front end pods needed to connect to a back end service - which of the multiple back end pods will it go to?
- A Kubernetes service groups these pods together 
	- For example, a service created for the backend pods will group all the backend pods together and provide a single interface for other pods to access this service
- The requests are forwarded to one of the pods randomly 
- Each service gets a name and an IP assigned to it - this is the name that will be used by other pods to access this service
- This type of service is called ClusterIP

#### Note

- There is a default ClusterIP given at launch from Kubernetes