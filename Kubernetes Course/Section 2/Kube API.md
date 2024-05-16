
- kube-apiserver is responsible for authenticating and validating requests, retrieving and updating data in the ETCD data store
- kube-apiserver is the only component that interacts directly with the ETCD data store
	- Other components uses the API server to perform updates in the cluster

#### Modes of authentication

- Authorisation
- Encryption
- Security

#### ETCD servers

- The option ETCD servers is where you specify the location of the ETCD servers - this is how kube apiserver connects to the ETCD servers
- So how do you view the kube-apiserver options in an existing cluster?
	- If you set it up with a kubeadmin tool, the kubeadmin deploys the kubeadmin-apiserver as a pod in the kube-system namespace in the master node