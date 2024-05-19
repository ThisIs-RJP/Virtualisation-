
#### What is Ansible

- Tool to automate IT tasks
- Declarative


#### Why use Ansible

- When you have a complex IT infrastructure, with many servers, it's very difficult to do these tasks manually
	- Maybe updating a new app, or software, just very repetitive tasks

#### Benefits of using Ansible

- Execute the tasks from your own machine
- Config/Installation/Deployment steps are in a single YAML file
- Re-use the same multiple files and for different environments
- More reliable, less likely to cause errors


#### Ansible is agentless!

- No need to install it on all the servers, just have it on one machine - can now manage servers remotely
	- No deployment effort in the beginning
	- No upgrade effort


#### How does Ansible work?

- Works in modules - small programs that actually do the work
	- Sent from the control machine, sent to the servers and do what they have to do - removed when they are done
- Modules do one small task, and another module to do another - they are granular, each one has their own task


#### Ansible Playbooks

- Ansible playbooks are essentially a set of instructions written in YAML that define the desired state of a computer system or a group of systems
	- How, in which order
	- What time
	- What modules should be executed
- You can execute a number of modules in a sequence
- Play - a set of instructions that targets a specific group of hosts (computers) and defines what tasks should be performed on them
	- You can have multiple plays in a single file
- Inventory - all of the machines involved in the task execution


#### Ansible Tower

- UI Dashboard from Red Hat
- Centrally store automation tasks
- Across teams
- Configure permissions
- Manage inventory