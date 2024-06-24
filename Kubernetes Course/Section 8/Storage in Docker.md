
#### How does Docker store the files of an image and a container?

When Docker builds images it builds these in a layered architecture
- Each line of instruction in the Docker file creates a new layer in the Docker image

###### Example 

From layer 1....

1. Base Ubuntu Layer
2. Changes in the packages
3. Changes in the pip packages
4. ....
5. 5


![[Pasted image 20240624181532.png]]

##### Image Layer

- Contains all of the steps that we need to carry out in a particular sequence to create a Docker Image so that it can be built to start up a container

##### Container Layer

- Where we run the image to start the container and then work on it and set up services on top of it

#### What if we would like to preserve the data created by a container

We add a persistent volume to the container


#### Volume mounting

- Refers to the process of attaching a storage volume to a container so that the container can read and write data to a persistent storage medium


#### Bind Mounting

- A method to link a specific folder or file on your computer to a folder or file inside a Docker container 

#### Storage Drivers

Docker uses storage drivers to enable layered architecture

