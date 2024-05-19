
#### DevOps tasks before automation

- If you want to create an application and you want to deploy it on server:
	- You would have to get some servers
	- Set up said servers
	- Configure networking in those servers
	- Create route tables
	- Install the software
	- Configure software
	- Install databases for the application
- Most of these things are done manually
	- High human resources cost
	- More effort and time
	- Higher chance of human error
- Then there's the problem with maintenance
	- Update versions
	- Deploy new releases
	- DB backups/updates
	- Recover app if something happens
	- Recover servers if something happens
	- Change network configuration

#### DevOps after automation

- No need to do anything manually - everything is automated using Infrastructure as Code

#### What is Infrastructure with Code (IaC)

- Automates the tasks end to end
	- End to end - Automating tasks without manual intervention
- So system admins pack their knowledge into programs and applications to be able to do this
- IaC is a concept
- IaC tools/programs, which carry out these tasks


### There are 3 main tasks categories of tasks

#### 1) Infrastructure Provisioning

- The first step
- Spinning new servers
- Setting up the network configuration
- Creating load balancers
	- Components that distribute incoming network traffic across multiple servers or instances to ensure high availability, reliability, and scalability of applications and services.
- Configuration other things on an infrastructure level


#### 2) Configuring the already provisioned infrastructure

- Installing applications on the servers
- Managing those applications
- This prepares the infrastructure/servers to deploy the app

#### 3) Deployment of the Applications

- Last step
- With Docker, the configuration (step 2) and deployment steps (step 3) can be merged
	- Take application and configuration and package it together
		- Configuration is already in the image, just run the container

#### Distinction of Phases

1. Initial Setup Phase
	- Provision infrastructure
	- Configure infrastructure
	- Initial installing and configuration of software

2. Maintaining Phase
	- Adjustment to the infrastructure
	- Add/Remove servers
	- Change network configuration
	- Updating software


#### Difference with IaC tools
- They automate tasks in different categories for different phases
- Most occasions, you will use a combination of 2 or more IaC tools 
- For example, Terraform can
	-  Provision Infrastructure
	- Manage Infrastructure
	- Be used for the initial application setup
	- But cannot manage the application
- However, Ansible, Puppet, and Chef can
	- Manage the application
	- be used for the initial application setup
	- Manage infrastructure
	- But cannot provision the initial setup
- That is why some people use a combination
	- Terraform to provision and configure infrastructure
	- Ansible to install and deploy applications
![[Pasted image 20240516100605.png]]


#### Difference between the IaC tools and how they work

### Declarative vs Procedural
##### Declarative

-  Declare end result
	- *"I want 2 servers"*

#### Procedural

- Step by step instruction
	1. Create a server
	2. Add a server
	3. Make this change


### Mutable vs Immutable

- Mutable - Make changes
- Immutable - Replace - make a new one, discard old