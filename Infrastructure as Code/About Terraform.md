
#### What is Terraform

- Terraform is an Infrastructure as Code tool that automates and manages your infrastructure
- Automates
	- Your platform
	- And services that run on that platform

- It is open source and
- <u>declarative</u>
	- Steps don't need to be specified, just specify the end result

#### But what is Terraform used for?

- Provisioning infrastructure
	- Create VPC (Virtual Private cloud)
		- A place where users can launch and manage their resources for their application
- Spin up servers
- Create AWS users with permissions
- Install Docker 

#### Managing Existing Infrastructure

- Create infrastructure
- Changes to the infrastructure
- All of the above are made easy using Terraform


#### Replicating Infrastructure

- Suppose you have tested your application setup and you want to release your application into a production environment
	- So in this case, you want the SAME infrastructure for production
- You can use Terraform for this

### How does Terraform work?

#### Terraform architecture
##### There are 2 main components that make up its architecture

#### 1) The Core

- Takes 2 input sources
	- TF-config (Terraforming configuration)
		- What to create/configure
	- Terraform's state
		- Current state of setup 
- The core takes these 2 inputs and makes a plan
	- What needs to be created, updated, destroyed?
	- Compares the current state and desired state
		- Decides on how to achieve the desired state from the current state

#### 2) Providers for technologies

- e.g AWS, Azure etc

Once the core has a plan, it uses the providers to execute the plan (connect to the platform and carry out the execution steps)

#### Terraform commands for different stages

- refresh - query the infrastructure provider to get the current state
- plan - create an execution plan
	- Determines what actions to take to achieve the desired state
	- Figures out what changes to make
- apply - execute the plan
- destroy - destroys the setup, resources in the correct steps
- 