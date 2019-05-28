## Kubernetes

- [Kubernetes on Ubuntu 18.10](https://www.linuxtechi.com/install-configure-kubernetes-ubuntu-18-04-ubuntu-18-10/)
- [How to Install and Configure Kubernetes and Docker on Ubuntu 18.04 LTS](https://www.howtoforge.com/tutorial/how-to-install-kubernetes-on-ubuntu/)

#### 1. Master

```bash
sudo hostnamectl set-hostname "k8s-master"
```

#### 2. Update `/etc/hosts` on master and slave

```bash
192.168.0.26    wk-MacBook.local
192.168.0.200   k8s-master
```

#### 3. Install Docker on mater and slave

#### 4. Disable swap

```bash
sudo swapoff -a
```

#### 5. Install Kubernetes

```bash
sudo apt-get install apt-transport-https curl -y
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"

sudo apt-get install kubeadm -y
kubeadm version

sudo kubeadm init --pod-network-cidr=172.168.10.0/24
sudo kubeadm init --pod-network-cidr=192.168.0.0/24 --apiserver-advertise-address=192.168.0.200

sudo kubeadm reset

mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config

```

#### 6. Tests

```bash
kubectl get nodes
kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node
kubectl describe deployments hello-node
kubectl get deployments
kubectl get pods
kubectl get events

kubectl get pods --output=wide

kubectl expose deployment hello-node --type=LoadBalancer --port=8080
kubectl delete deployment hello-node
kubectl get services
kubectl delete service hello-node
```

```bash
kubectl run hello-world --labels="run=load-balancer-example" --image=gcr.io/google-samples/node-hello:1.0  --port=8080
kubectl get deployments hello-world
kubectl describe deployments hello-world

kubectl expose deployment hello-world --type=NodePort --name=my-service
kubectl delete deployment hello-world

kubectl get services my-service
kubectl delete service my-service

```

```bash
kubectl run bootcamp --image=docker.io/jocatalin/kubernetes-bootcamp:v1 --port=8080
kubectl get deployments
kubectl expose deployment/bootcamp --type="LoadBalancer" --port 8080
kubectl get services
```

```bash
kubectl get pods
kubectl proxy
```

