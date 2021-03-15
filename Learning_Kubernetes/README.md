# Learn Kubernetes (K8s)

## Introduction

### Definition
An Open-source platform designed to automate deploying, scaling and operating application containers
 
### Goal
	To foster an ecosystem of components and tools that relieve the burden of running applications in public and private clouds

### Features

* Multi-Host Container Scheduling
* Scalability and Availability
* Flexibility and Modularization
* Registration and Service Discovery
* Persistent Storage
* Application Upgrades and Downgrades
* Maintenance
* Logging and Monitoring
* Secrets Managements
* Community

### Terminology
* Node
	The node serves as a worker machine in K8s cluster. One important thing to note is that the node can be a physical computer or a virtual machine.
	* Requirements
		* A kubelet running
		* Container tooling like Docker
		* A kube-proxy process running
		* Supervisord

* Pod
	The simplest unit that you can interact with. You can create, deploy, and delete pods, and it represents one running process on your cluster.
	* Docker Container
	* Storage Resource
	* Unique network IP
	* Options that govern how the container(s) should run
	* Pod States
		* Pending
		* Running
		* Succeeded
		* Failed
		* CrashLoopBackOff

* ReplicaSets
	Ensures that specified number of replicas for a pod are running at all times.
* Deployments
	A Deployment controller provides declarative updates for pods and ReplicaSets.
* DaemonSets
	DaemonSets ensure that all nodes run a copy of a specific pod.
	As nodes are added or removed from the cluster, DaemonSet will add or remove the required pods.
* Jobs
	Supervisor process for pods carrying out batch jobs
	Run individual processes that run once and complete successfully
* Services
	Allow the communication between one set of deployments with another
	Use a service to get pods in two deployments to talk to each other
	* Types
		* Internal: IP only reachable within the cluster
		* External: Endpoint available through node ip: port (called NodePort)
		* Load balancer: Exposes application to the internet with a load balancer (available with a cloud provider)
	
* Labels
	Labels are key/value pairs that are attached to objects like pods,services, and deployments. Labels are for users of Kubernetes to identify attributes for objects. 
* Selectors
	* Equality-based
		* Two labels or values of labels should be equal.
		* The values of the labels should not be equal.
	* Set-based
		* IN: A value should be inside a set of defined values
		* NOTIN: A value should not be in a set of defined values
		* EXISTS: Determines whether a label exists or not
* Namespaces
	* Great for large enterprises
	* Allows teams to access resources, with accountability
	* Great way to divide cluster resources between users
	* Provides scope for names must be unique in the namespace

* Kubelet
	The Kubelet is the "Kubernetes node agent" that runs on each node
	* Roles
		* Communicates with API server to see if pods have been assigned to nodes
		* Executes pod containers via container engine
		* Mounts and runs pod volumes and secrets
		* Executes health checks to identify pod/node status
* kube-proxy
	* Process that runs on all worker nodes
	* Reflects services as defined on each node, and can do simple network stream or round-robin forwarding across set of backends 
	* Service cluster IPs and ports are currently found through Docker --link compatible environment variables specifying ports opened by the service proxy
	* Modes
		* User space mode
		* Iptables mode
		* Ipvs mode (alpha feature)


### Architecture

* Master Node
	* The API Server
	* Scheduler
	* Controller Manager
* etcd
* kubectl
	* kubeconfig
* Work Node
	* kubelet
	* Docker
		* pod
			* containers 
	* kube-proxy
* Internet
* End-User

## Working with Kubernetes

### Packages Required
* kubectl 
* minikube

### Getting started
* Start minikube 
	```
	minikube start
	```
* To see all Kubernetes Application
	```
	kubectl get all
	```
* To create Kubernetes Application from yaml file
	```
	kubectl create -f <filename>.yaml
	```
* To expose deployment
	```
	kubectl expose deployment <filename> --type=NordPort
	```
* To see the exposed deployment
	```
	minikube service <filename>
	```

