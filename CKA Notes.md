# Core Concepts
## Cluster Architecture
- Worker nodes host applications as containers 
	-  Containers - Applications
		- container runtime application
		- Need something like docker to be installed on the worker nodes
	- kubelet - agent that runs on each node on the cluster
		- Listens for instructions from kube-apiserver to destroy or create nodes as needed
	- kube-proxy - enables necessary rules are in place on container nodes to allow communication between worker nodes
- Master node plan manager schedule and monitor nodes
	- Done with control plane components
	- ETCD cluster - is a database stored in Key:value format
	- Kube-scheduler - identifies the right node to place a container on based on worker nodes, capacity, taints, tolerations etc
	- Controller Manager 
		- Node controller - responsible for onboarding new nodes to the cluster
		- Replication controller - ensures desired number of containers are greated
	- kube-apiserver - responsible for orchestrating all operations within the cluster
		- Exposes k8s api to users and controllers
		- Used by worker nodes to communicate to the server
## Docker vs Containderd
- 
