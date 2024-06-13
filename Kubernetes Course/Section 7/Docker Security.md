

Process isolation in containers means that each container has its own set of processes, namespaces, and resources, ensuring that processes within a container cannot see or interact with processes in other containers or the host system.

A root user in Linux is like an administrator

Docker implements a set of security features that limits the abilities of the root user within the container - since the root user generally is able to do anything

By default, Docker runs a container with a limited set of capabilities 
- This means that processes running within the container won't have privileges to do stuff like reboot the container that can disrupt other applications