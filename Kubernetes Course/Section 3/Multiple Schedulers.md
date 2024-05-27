
#### Intro

- A Kubernetes cluster can have multiple schedulers at a time
- When creating a pod or deployment, you can instruct Kubernetes to have the pod scheduled by a specific scheduler
	- Multiple schedulers must have different names - so that we can identify them as separate schedulers

#### If we were to deploy the scheduler as a pod

- Create the pod definition file
- Specify the kubeconfig property, which is the path to the scheduler conf file

#### Leader elect

- Used when you have multiple copies of the scheduler running on different master nodes as a high-availability setup where you have multiple master nodes with the Kubernetes scheduler process running on both of them
	- If multiple copies of the same scheduler are running on different nodes only one can be active at a time, and that's where the leader elect option helps in choosing a leader who will lead the scheduling activities

#### What is the benefit of multiple schedulers

- Multiple schedulers in Kubernetes allows for tailored scheduling policies, better resource utilisation, and enhanced control over workload placement, leading to improved performance and flexibility in managing diverse applications and requirements.