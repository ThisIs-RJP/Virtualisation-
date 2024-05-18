
#### How you might want to deploy your application

- Suppose you have a web server that needs to be developed 
	- You need not one, but many such instances of the web servers running for obvious reasons
- Secondly, whenever newer versions of application bills become available on the Docker Registry, you would like to upgrade your instances seamlessly. 
- However, when you upgrade your instances, you do not want them to upgrade all at once
	- This may impact users accessing our applications so you might want to upgrade them one after the other
- This process is called rolling updates
- Suppose one of the upgrades you performed resulted in an unexpected error and you're asked to undo the changes
	- You would like to be able to roll back the changes that were carried out 
- Finally, suppose you would like to make multiple changes to your environment such as upgrading the underlying web server versions as well as scaling your environment and also modifying the resource allocations etc 
	- You don't want to apply each change immediately after the command is run
- Instead you would like to apply a pause to your environment, make the changes, and then resume so that all the changes are rolled out together 
- All of these capabilities are available with the Kubernetes deployments  

#### About deployment

- Deployment is a Kubernetes object that comes higher in the hierarchy
	- The deployment provides us with the capability to upgrade the underlying instances seamlessly using rolling updates, undo changes, pause, and resume changes as required

#### How do we create a deployment definition file

- Similar to the ReplicaSet definition file, except ```kind``` will be deployment