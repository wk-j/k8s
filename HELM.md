## Helm

```bash
curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh
chmod 700 get_helm.sh
./get_helm.sh
helm init
helm search
helm install stable/jenkins

kubectl get services
minikube service unsung-billygoat-jenkins
```