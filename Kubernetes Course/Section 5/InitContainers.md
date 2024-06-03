
In a multi-container pod, each container is expected to run a process that stays alive as long as the pod's lifecycle.
	E.G A multi container pod that has a web application and a logging agent are both containers that are expected to stay alive at all times - if either fails, the pod restarts

But at times you may want to run a process that runs to completion in a container, a one time task let's say.
	E.G A process that pulls a code or binary from a repository that will be used by the main web application. 

- This is what initContainers are for

#### About initContainers

- When a pod is first created the initContainer is run, and the process in the initContainer must run to a completion before the real container hosting the application starts
- If any of the initContainers fail to complete, Kubernetes restarts the pod repeatedly until the initContainer succeeds