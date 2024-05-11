
# What is Docker?

- Docker is a software development platform that makes it easy to develop and deploy apps inside of a neatly packaged virtual containerised environments
	- In simple terms, Docker is a tool used to package software applications and their dependencies into small, standardised units called containers. These containers can be easily moved, deployed, and run on any machine that has Docker installed, regardless of the underlying operating system.
		- It's kind of like a lightweight, portable package that contains everything your application needs to run smoothly to make development and deployment more efficient
	- This means apps run the same, no matter where they are or what machine they're running on

- Each container running on a computer are like little micro computers, each with their own specific jobs, their own OS and their own isolated CPU, memory and network resources
	- This means, you can be added, removed, stopped and started again without interrupting other containers and the host machine
- Containers usually run one specific task (MySQL database, NodeJS Application) and are networked together and potentially scaled

### Details about Docker

- Developers typically access DockerHub, an online repository of Docker containers and pull one containing a pre-configured environment for their specific programming language (e.g Ruby, NodeJS) with all their libraries and frameworks to get started

# Docker vs VM

- VM have to quarantine off a set amount of resources, then the VM has to communicate with the host computer via a hypervisor
- Docker containers share the same OS kernel as the host machine, but they are isolated from each other. This means they are more lightweight and efficient than VM's
- Docker containers are faster to deploy because don't need to boot an entire OS
- Docker containers are highly portable because they encapsulate the app and its dependencies into a single package, and these containers can run on any machine that has Docker installed
	- VM's are less portable because they include an entire OS, more complex than Docker containers
- VM's are more suited for running applications that require full OS isolation
	- Docker is more suitable for microservices architecture, continuous integration and deployment and containerised applications that require fast and efficient deployment
- Docker uses less disk space - reuses files by using a layered file system
	- If you have multiple docker images using the same base image for instance, Docker will only keep a single copy of the image and share them between containers

# About Docker

- Start with a Dockerfile > Docker image > run as a Docker Container

### Dockerfile
- A text file document that instructs how the Docker image will be built
- First select a base image to start with the keyword ```FROM``` which you can find a container to use from the Dockerhub 
	```FROM ubuntu:22.04```
- Now, you can run commands, such as downloading, installing and running your software
	```RUN echo "Thanks for watching"```

### Docker images
- When we're finished, we can start building
	- Build using ```docker build```
	- Example
		```docker build -t myDockerImage .```
- Verify the image's existence using ```docker images```
- Now using the built image, you can run a container of that image

### Docker container

- To run a container, pull it down from Dockerhub, or build the image you already have
	```docker run myDockerImage```

- Extra tags
	- ```-d``` = Detached mode: 
		- Detached mode in Docker refers to running a container in the background without attaching to its standard input (stdin), output (stdout), and error (stderr) streams. When you run a Docker container in detached mode, you can continue to use your terminal for other tasks without being attached to the container's console.
- You can view your running containers using
	```docker container ls```
	