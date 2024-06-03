
#### Problem with Ubuntu Images

 - Suppose you were to run a Docker container from an Ubuntu image
 - When you run the Docker run Ubuntu command, it runs an instance of Ubuntu image and exits immediately and you wouldn't see the container running
	 - If you list all containers you will see that the new container you ran is in an exited state
- Containers are not meant to host an OS - they run a specific task (host an instance of a web server, application server, or database)
	- Once the task is complete, the container exits
	- A container only lives as long as the process inside it is alive
		- If a service in the container stops, the container exits
- When you run the Docker file for an Ubuntu image, you will see that bash is the default command
	- Bash is not a web server or a database server, it is a shell that listens for inputs from a terminal - if it can't find the terminal it exits
- By default, Docker does not attach a terminal to a container when it is run, so the bash program does not find the terminal and exits

#### How do you specify a different command to start the container?

###### Append a command to the Docker run command

- Overrides the default command specified within the image
	- So when you run `docker run ubuntu sleep 5` as the added option, the container starts and runs the `sleep` program, and exits

#### How do you make that change permanent?

- Create your own image from the base Ubuntu image and specify a new command

#### Entry Point Instruction

- You can specify the program that will be run when the container starts
- Whatever you specify on the command line will be appended to the entry point

![[Pasted image 20240528131410.png]]

