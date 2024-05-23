
#### What does Node Affinity do?

- Ensure that pods are hosted on particular nodes
	- I.E, ensure the large data processing pod ends up on nodes one (a node that will have enough resources if the job demands more)
- Node Selectors and Node Affinity both control pod scheduling - but they do it in different ways
	- Node Affinity is more complex. That said, it allows for more flexibility - more expressions, conditions and preferences
- Let's say you can have the pod be placed in a large or medium node
	- All you have to do is have a list of values for where your pod can end up in
		![[Pasted image 20240521235335.png]]

