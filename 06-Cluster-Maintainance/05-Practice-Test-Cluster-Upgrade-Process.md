# Practice Test - Cluster Upgrade Process
  
Solutions to practice test cluster upgrade process
- What is the current version of the cluster?
  
  <details>
  ```
  $ kubectl get nodes
  ```
  </details>
  
- How many nodes are part of this cluster?
  
  <details>
  ```
  $ kubctl get nodes
  ```
  </details>
  
- Check what nodes the pods are hosted on.
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
  
- Count the number of deployments
  
  <details>
  ```
  $ kubectl get deploy
  ```
  </details>
  
- Run the command kubectl get pods -o wide
  
  <details>
  ```
  $ kubectl get pods -o wide
  ```
  </details>
  
- You are tasked to upgrade the cluster. User's accessing the applications must not be impacted. And you cannot provision new VMs. What strategy would you use to upgrade the cluster?
  
  <details>
  ```
  Upgrade one node at a time while moving the workloads to the other
  ```
  </details>
  
- Run the kubeadm upgrade plan command
  
  <details>
  ```
  $ kubeadm upgrade plan
  ```
  </details>
  
- Run the kubectl drain master --ignore-daemonsets
  
  <details>
  ```
  $ kubectl drain master --ignore-daemonsets
  ```
  </details>
  
- Run the command apt install kubeadm=1.18.0-00 and then kubeadm upgrade apply v1.18.0 and then apt install kubelet=1.18.0-00 to upgrade the kubelet on the master node
  
  <details>
  ```
  $ apt install kubeadm=1.18.0-00
  $ kubeadm upgrade apply v1.18.0 
  $ apt install kubelet=1.18.0-00
  ```
  </details>
  
- Run the command kubectl uncordon master
  
  <details>
  ```
  $ kubectl uncordon master 
  ```
  </details>
  
- Run the command kubectl drain node01 --ignore-daemonsets
  
  <details>
  ```
  $ kubectl drain node01 --ignore-daemonsets
  ```
  </details>
  
- Run the commands: apt install kubeadm=1.18.0-00 and then kubeadm upgrade node. Finally, run apt install kubelet=1.18.0-00.
  
  <details>
  ```
  $ apt install kubeadm=1.18.0-00
  $ kubeadm upgrade node
  $ apt install kubelet=1.18.0-00
  ```
  </details>
  
- Run the command kubectl uncordon node01
  
  <details>
  ```
  $ kubectl uncordon node01
  ```
  </details>

  -------------------------

  Question: Upgrade the controlplane components to exact version v1.25.0

Upgrade the kubeadm tool (if not already), then the controlplane components, and finally the kubelet. Practice referring to the Kubernetes documentation page.
Note: While upgrading kubelet, if you hit dependency issues while running the apt-get upgrade kubelet command, use the apt install kubelet=1.25.0-00 command instead.


On the controlplane node, run the following commands:

This will update the package lists from the software repository.

` apt update `


This will install the kubeadm version 1.25.0

` apt-get install kubeadm=1.25.0-00 `


This will upgrade Kubernetes controlplane node.

` kubeadm upgrade apply v1.25.0 `


    Note that the above steps can take a few minutes to complete.


This will update the kubelet with the version 1.25.0.

` apt-get install kubelet=1.25.0-00 `


You may need to reload the daemon and restart kubelet service after it has been upgraded.

```
systemctl daemon-reload
systemctl restart kubelet
```

