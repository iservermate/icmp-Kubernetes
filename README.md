# icmp-k8
iServermate K8 Project

Links:
Oracle VirtualBox:  https://www.virtualbox.org/

Vagrant: https://www.vagrantup.com/

Link to download VM images: http://osboxes.org/

Link to kubeadm installation instructions: https://kubernetes.io/docs/setup/independent/install-kubeadm/

Install and set up the kubectl tool: https://kubernetes.io/docs/tasks/tools/

Install Minikube: https://minikube.sigs.k8s.io/docs/start/

Install VirtualBox: https://www.virtualbox.org/wiki/Downloads
                    https://www.virtualbox.org/wiki/Linux_Downloads



Minikube Tutorial: https://kubernetes.io/docs/tutorials/hello-minikube/

If the minikube installation has been done on the macOS, then to access the URL on the local browser, we need to do a few steps to get the service URL to work. Those steps are covered on this documentation page: https://minikube.sigs.k8s.io/docs/handbook/accessing/#using-minikube-service-with-tunnel



Newtorking Addons (Weave Net): https://kubernetes.io/docs/concepts/cluster-administration/addons/


#Ref: https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/#pod-network:~:text=Initializing%20your%20control,plane%20node%20run%3A

Note: Control plane node isolation - By default, your cluster will not schedule Pods on the control plane nodes for security reasons. If you want to be able to schedule Pods on the control plane nodes, for example for a single machine Kubernetes cluster, run:
- name: Untaint the node
  shell: kubectl taint nodes --all node-role.kubernetes.io/control-plane-
  become: false
  run_once: true
  when: 
    - ansible_hostname == MasterHostName
    - PodNetworkAddon == flannel


#Note: If you do set the --cluster-cidr option on kube-proxy, make sure it matches the IPALLOC_RANGE given to Weave Net (see below).
#Run this commands on Master node 
  #kubectl get ds -AT
  #kubectl edit ds weave-net -n kube-system
  #Add new env: variable in running configs

#If facing this below error run this command **"$ KUBECONFIG=$HOME/.kube/config"**

  root@icmp-master01 ~]# kubectl get pods -A
  E0630 20:10:29.495216   23564 memcache.go:265] couldn't get current server API group list: Get "http://localhost:8080/api?timeout=32s": dial tcp 127.0.0.1:8080: connect: connection refused
  
