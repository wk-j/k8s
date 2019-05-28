## Kubernetes

- [Kubernetes on Ubuntu 18.10](https://www.linuxtechi.com/install-configure-kubernetes-ubuntu-18-04-ubuntu-18-10/)

### 1. Master

```bash
sudo hostnamectl set-hostname "k8s-master"
```

### 2. Update `/etc/hosts` on master and slave

```bash
192.168.0.26    wk-MacBook.local
192.168.0.200   k8s-master
```

### 3. Install Docker on mater and slave

### 4 Disable swap

```bash
sudo swapoff -a
```

### 5. Install Kubernetes

```bash
sudo apt-get install apt-transport-https curl -y
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"

sudo apt-get install kubeadm -y
kubeadm version

sudo kubeadm init --pod-network-cidr=172.168.10.0/24

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

kubectl get nodes
```