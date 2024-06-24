
A PVC in Kubernetes is like a request for storage by an application.
Once the PVC's are created, Kubernetes binds the PV's to claims based on the request and properties on the volume

- If there are multiple possible matches, you can use labels and selectors to bind to correct volumes
- If there are no volumes available, the persistent volume claim will remain in a pending state
- Once newer volumes are available, the claim would automatically be bound to the newly available volume