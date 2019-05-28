## Minikube

```bash
brew cask install virtualbox
brew cask install minikube
minikube start

brew cask remove virtualbox
brew cask remove minikube
brew uninstall kubectl
```

```bash
sudo apt-get install -y virtualbox virtualbox-ext-pack
curl -Lo minikube https://storage.googleapis.com/minikube/releases/v0.28.2/minikube-linux-amd64
chmod +x minikube && sudo mv minikube /usr/local/bin/

minikube dashboard

kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.4 --port=8080
kubectl expose deployment hello-minikube --type=NodePort
minikube service hello-minikube

kubectl get services

```