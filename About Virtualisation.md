
#  Introduction

### What is a virtual machine (VM) ? 

In computing, a virtual machine is the virtualisation or emulation of a computer system.
- It is a digital version of a physical computer that can run programs and other OS's, store data, connect to networks and do other computing functions
- Virtual machines allows users to use other OS's without a separate physical hardware to install an OS
	- Instead, they can install it on their host OS (the OS already installed on their device)
- A hypervisor allows users to hosting multiple virtual computers on one singular physical computer
	- Most popular one is <u>VirtualBox</u>
		- VirtualBox takes hardware resources from Host OS
		- Creates virtual CPU, virtual RAM, virtual storage for each virtual machine
		- Only give resources that the computer actually has
			- Hardware resources are shared between the OS's
- Virtual Machines don't see other virtual machines IE, they are completely isolated
	- Separation is important - if something happens to one of the machines, it wont affect the <u>main</u> OS

# What is the benefit of having a hypervisor?

- Very good for learning other OS - just host it on your current OS
	- Can do so without endangering the main OS
- Test applications on other OS's

# Type 2 Hypervisors

- Also known as hosted hypervisors
- Type 2 Hypervisors - Creating a virtual machine on top of an existing OS
	- With host OS
	- Using VirtualBox, etc
- Using the shared resources from the host OS, *guest* OS's can be used
- Typically used for personal computers


# Type 1 Hypervisors

- Works the same way as Type 2, but instead of installing the OS on the existing OS, it is installed directly to the hardware
- Also known as bare metal hypervisors
	- Controls hardware resources instead of talking to the host OS
- Used for big servers and companies 
- Popular choices include
	- VMWare ESXi
	- Microsoft Hyper V
- For big servers you have 1 physical server with a bare metal hypervisor installed on it and multiple virtual machines that are running on that hypervisor, all sharing the same resources

# Type 1 Hypervisor use cases

- When you create a server instance on a cloud platform, you are creating the virtual machines on a physical server
- Other users that creates instances will get a virtual machine in that same server as your virtual machine
	- The VM's are isolated - nothing happens if something happens to one of the VM's 
		- They don't share resources

# Benefits of Type 1 Hypervisor

- Using virtualisation and hosting multiple VM's on one physical machine:
	- Results in efficient usage of hardware resources
	- Users can choose any resource combination
		- Flexibility of choosing the size of their instances because everything is virtual
			- Cloud providers can use up all physical resources by dividing them into small pieces that are used by VM's
- Abstraction of the OS from the hardware
- Without virtualisation, for example
	- Company managed their own servers
	- Installing applications
	- OS is now tightly coupled to the hardware
		- If the hardware fails, the whole computer is useless - the OS, applications and data would be lost
	- Relying on one box resulted in one point of failure
- With virtualisation, the OS is a portable file
	- This includes the OS, applications, data
	- Since it is a file, it can be copied
	- It can be moved around, not reliant on a physical server
- If something happens to an OS, or an application fails or hardware breaks
	- You can take the image/snapshot, run it on a different computer that has hypervisor