# Core Concepts
## Cluster Architecture
- Worker nodes host applications as containers 
- Master node plan manager schedule and monitor nodes
	- Done with control plane components
	- ETCD cluster - is a database stored in Key:value format
- Kube-scheduler - identifies the right node to place a container on based on worker nodes, capacity, taints, tolerations etc
- Controller Manager 
- Node controller - responsible for onboarding new nodes to the cluster
- Replication controller - ensures desired number of containers are greated