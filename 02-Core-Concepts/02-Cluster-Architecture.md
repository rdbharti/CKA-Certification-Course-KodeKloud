In this section , we will take a look at the kubernetes Architecture at high level.

  ![Kubernetes Architecture](../images/k8s-arch.PNG)
  
  ![Kubernetes Architecture 1](../images/k8s-arch1.PNG)

## etcd

- its database 
- It stores data in a key-value format

## kube-scheduler

- It identifies the right node to place the conatiner on based on
  - containers resourse requirement
  - the worker node capacity
  - any other policies or constarints, such as
    - taints and tolerations
    - node affinity rules

## Node-Controller and Replication Controller

-  Node-Controller
   -  Respopnsible for onboarding new node on cluster
   -  Handling situations where the nodes become unavailable
- Replication Controller
  - Responsible to look for desired number of containers running

- **Control-Maneger** = Node-Controller + Replication-Controller
  
## kube-apiserver

- It is the primary management component of k8s
- Responsible for orchestrating all operations within the cluster
- Exposes k8s api to user to manage clusters as well as various controllers to monitor state of the cluster and make necessary changes.

## container runtime engine (Docker)

- Container engine must be installed on all the nodes including the master node.

## kubelet

- It is an agent that runs on each node in the cluster
- It listens for instructions from kube-api server to destroy containers or nodes
- sends information to kube-apiserver to monitor the status of nodes and containers.

## Kube-Proxy

- It communicates among the worker-nodes
- It ensures the necessary rules are in place on worker-nodes to allow the containers running on them to reach one another.


K8s Reference Docs:
- https://kubernetes.io/docs/concepts/architecture/