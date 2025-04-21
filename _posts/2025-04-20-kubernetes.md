---
title: Instructions for Kubernetes
date: 2025-04-20 12:00 -000
categories: [softwarw]
tags: [kube, dicas]              # Tag always lowercase
---

## Kubernetes

### #micrik8s

microk8s add-node\
microk8s add-node --token-ttl 3600

From the node you wish to join to this cluster, run the following:\
```
microk8s join 192.168.0.169:25000/f3fd03a0a6ac93f881b553b12725a9b1/667a3ef27bfd

microk8s join 192.168.0.169:25000/6de8a0b631d59ad4ddc6f9a7ec2d3537/5c9691d3d674
```
Use the '--worker' flag to join a node as a worker not running the control plane, eg:\
```
microk8s join 192.168.0.169:25000/f3fd03a0a6ac93f881b553b12725a9b1/667a3ef27bfd --worker
```
If the node you are adding is not reachable through the default interface you can use one of the following:\
```
microk8s join 192.168.0.169:25000/f3fd03a0a6ac93f881b553b12725a9b1/667a3ef27bfd
```

sudo snap install microk8s --classic
```
sudo usermod -a -G microk8s thor
mkdir -p ~/.kube
chmod 0700 ~/.kube
sudo chown -f -R thor ~/.kube
newgrp microk8s
```

echo "alias kubectl='microk8s kubectl'" >> ~/.bash_aliases
source .bash_aliases

microk8s dashboard-proxy

(https://medium.com/@muppedaanvesh/deploying-nginx-on-kubernetes-a-quick-guide-04d533414967)

### k3s

## create a deployment
kubectl create deployment nginx --image=nginx
kubectl create service nodeport nginx --tcp=80:80

## create a pod
kubectl run nginx-pod --image=nginx --restart=Never --port=80 -n default
## createa service
kubectl expose pod nginx-pod --type=NodePort --port=80 --name=nginx-service
## Delete the service
kubectl delete service nginx-service
## Delete the pod
kubectl delete pod nginx-pod


for k3s
sudo ufw disable
sudo swapoff -a
free -h
sudo nano /etc/fstab
sudo apt install apt-transport-https curl ca-certificates gnupg2 software-properties-common -y
curl -sfL https://get.k3s.io | sh -
sudo cp /etc/rancher/k3s/k3s.yaml ~
sudo chown -R thor k3s.yaml
export KUBECONFIG=~/k3s.yaml

" echo 'export KUBECONFIG=~/k3s.yaml' >> ~/.profile
  source ~/.profile
"

kubectl config view

kubectl get nodes -o wide

sudo cat /var/lib/rancher/k3s/server/node-token
curl -sfL https://get.k3s.io | K3S_URL=https://192.168.0.150:6443 K3S_TOKEN=K105cf4c8dcf6e2ba48b78d26b1a05f48f4eb97e9f352a51a2d0e7ee1eeca752ecc::server:1141f55d1707a85c35f321ecfb74dd59 sh -

curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--write-kubeconfig-mode=644" sh -
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--write-kubeconfig-mode 644" sh -

/usr/local/bin/k3s-uninstall.sh
/usr/local/bin/k3s-agent-uninstall.sh

# Links

http://rino.kozow.com/devops/posts/k3s-kubernetes-workshop-using-proxmox-server/

https://nvtienanh.info/blog/cai-dat-kubernetes-cluster-tren-ubuntu-server-22-04
https://www.youtube.com/watch?v=iwlNCePWiw4

{% include embed/youtube.html id='U1VzcjCB_sY' %}

https://www.youtube.com/watch?v=U1VzcjCB_sY&t=2002s

https://medium.com/@syed_usman_ahmed/setting-up-k3s-on-a-linux-virtual-machine-e5ffec09aeaf


https://www.portainer.io/blog/proxy-and-load-balance-your-microk8s-services-using-ingress-and-metallb-with-portainer

https://www.cherryservers.com/blog/install-kubernetes-ubuntu

https://www.youtube.com/watch?v=SUk_Nm5BiPw

kubernetes-a-quick-guide

kubeadm token generate
kubeadm token create <kubeadm token generate> --print-join-command
kubeadm join 192.168.0.232:6443 --token 735q50.pud5qo976cb13n80 --discovery-token-ca-cert-hash sha256:c2793093ee8d4d221049c95934e779b275c02ed86bfb56715f45ce77c8535704

{% include embed/youtube.html id='DrcS4jrA_no' %}

https://www.youtube.com/watch?v=DrcS4jrA_no&t=2809s

kubeadm init --apiserver-advertise-address 192.168.0.230 --pod-network-cidr 10.244.0.0/16 --cri-socket unix:///var/run/containerd/containerd.sock
