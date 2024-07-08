
In the world of Kubernetes, there are a lot of container solutions for networking, all pretty much doing the same thing.

What if you wanted to make your own program to do it too?
You would need to follow a set of standards

#### What are standards

Standards define how a program should look so that everyone can adhere to a single set of standards

#### Now, what is CNI then?

###### Container Network Interface => CNI

- A set of standards that define how programs should be developed to solve networking challenges

#### What does CNI consist of

- Defines a set of responsibilities for container run times and plugins
- Responsible for creating a network name space for each container
- Should identify the networks the containers must attach to
- Container run time should also invoke the plugin when its been deleted
- Also specifies how to configure a network plugin

###### On the plugin side

- It should support add, delete and check command line arguments
	- Should also accept parameters
- Should take care of assigning IP addresses to the pods

#### Note about Docker

Docker does not implement CNI

- It has its own set of standards CNM => Container Network Model
- You can't run a Docker container and specify the network plugin to use CNI