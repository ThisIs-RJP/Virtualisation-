
#### What would you like to monitor

- Node-level metrics
- How many of them are healthy
- Performance metrics
	- CPU
	- Memory
	- Network
	- etc..
- The number of pods
- The performance metrics of each pod
	- CPU consumption
	- Memory consumption

###### There are a number of open-source solutions available

- Metrics Server
- Prometheus

Proprietary solutions include
- Datadog
- Dynatrace

#### The Kubernetes Metrics Server

- A tool that collects and provides resource usage statistics, such as CPU and memory usage, for the nodes and pods within a Kubernetes cluster
- Only an in-memory monitoring solution - does not store the metrics
	- Cannot see historical performance data

#### How are metrics generated for the pods on these nodes

- Kubernetes runs an agent on each node known as a kubelet, which is responsible for receiving instructions from the Kubernetes API master server and running pods on the nodes
	- Kubelet also contains a sub component - cAdvisor and Container Advisor
- cAdvisor - responsible for retrieving performance metrics from pods and exposing them through the kubelet API to make the metrics available for the Metrics Server