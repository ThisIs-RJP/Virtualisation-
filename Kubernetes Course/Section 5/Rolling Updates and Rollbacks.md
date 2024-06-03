
#### Understanding rollouts

- When you first create a deployment, it triggers a rollout
- A new rollout creates a new deployment revision
- In the future when the application is upgraded, meaning when the container version is updated to a new one, a new rollout is triggered and a new deployment revision is created

#### Remember! Rollouts vs Revisions

###### Revisions
- A snapshot of the state of a Deployment at a particular point in time

###### Rollout
- The process of applying changes to a Deployment and updating the application's pods to reflect a new config specified in the latest version

#### There are 2 types of deployment strategies

1. Destroy all of the old versions and then create the newer versions of the application instances 
	- Destroy, then deploy
	- **Note:** This means that there is downtime when before the newer versions are up after the older ones are destroyed
	- This is known as the **recreate strategy** and is not the default deployment strategy
2. No destroying, we take down the older version then bring up the newer version
	- Application is never down, upgrade is seamless


#### How does a deployment perform an upgrade

- When a new deployment is created, it creates a replica set automatically and deploys 5 replicas
- When you upgrade your application, the deployment object creates a new replica set under the hood and starts deploying the containers there and at the same time, taking down the pods in the old replica set 

#### What if something went wrong?

- Kubernetes deployments allow you to roll back to a previous revision
- The deployment will then destroy the pods in the new replica set and bring the older ones up in the old replica set
-   