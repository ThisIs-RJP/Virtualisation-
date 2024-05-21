
#### Declarative commands in relation to objects

- Use the ```kubectl apply``` command to manage objects 
	- Intelligent enough to create an object if it doesn't already exist
- If there are multiple object configuration files, you can specify the directory as the path to that file
- If there are multiple object configuration files, specify the directory instead of just the path
	- This way, all the objects are created at once
- If we need to update an object config file, just run the ```kubectl apply``` command again
	- This time, it knows it exists so it updates it instead