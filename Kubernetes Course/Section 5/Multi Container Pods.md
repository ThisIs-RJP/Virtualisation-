
Idea of decoupling a large monolithic application into sub components known as microservices enables us to develop and deploy a set of independent, small, and reusable code.

- This architecture can then help us scale up, down as well as modify each service as required as opposed to modifying the entire application

###### However, sometimes you may need 2 services to work together

- This is why you need multi container pods that share the same life cycle
	- This means they are created together and destroyed together
	- They share the same network space - means they can refer to each other as local host and they have access to the same storage volumes
		- They can communicate with each other and access shared data because they have access to the same storage volumes