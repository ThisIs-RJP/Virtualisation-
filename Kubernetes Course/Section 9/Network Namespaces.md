
#### What is a network namespace

A network namespace is like a separate, isolated copy of the network stack in a Linux system.

Imagine it as a virtual network environment where you can have its own set of network interfaces, IP addresses, routing tables, and firewall rules, completely independent from those in other network namespaces or the main network stack of the host system


#### What if you had multiple namespaces and all of them needed to communicate with each other

- You create a virtual network inside your host
	- To do this, you need a switch
- Create a virtual switch within the host and connect namespaces to it
	- We can do this by creating an internal bridge network by adding an interface to the host
		- Remember that an interface is a point of interaction between systems - it's kind of like a bridge
- For namespaces, the interface is like a switch
	- For the host, it is an interface

#### What if I tried to reach one of these interfaces through my host?

- It won't work
- Host is on one network, namespaces are on another
	- Remember, the virtual switch is the interface for the host

#### From the namespaces...

- The only way to access the outside world is through the Ethernet port
- If it tries to access an IP outside of the network, it'll go to the routing table to which it will return "network unreachable" because it has no information about that network 
	- How do we find that gateway?
		- Remember that a gateway is a system that connects to the other networks

#### About NAT

NAT (Network Address Translation) IP table is a mechanism used by routers and firewalls to manage and translate IP addresses between a private network and the public internet.

