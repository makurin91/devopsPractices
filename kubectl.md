`https://minikube.sigs.k8s.io/docs/start/`


* Install `brew install minikube` and `brew install kubectl`
* Start `minicube start`
* Check ps with minicube `ps aux | grep minikube`
  
install hello minicube
```
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube --type=NodePort --port=8080
kubectl get services hello-minikube
minikube service hello-minikube
kubectl port-forward service/hello-minikube 7080:8080
```

* Output hello-minicube `kubectl logs -l app=hello-minikube`
* Minicube addons list `minikube addons list`
* Get list of nodes `kubectl get nodes -o wide`
* Get the description of a specific node `kubectl describe node <node-name>`
* Get all events in all namespaces `kubectl get events --all-namespaces`
* Get the description of the minicube `kubectl describe deployment hello-minikube`
* Get pod info `kubectl get pods -l app=prometheus -n <имя-неймспейса>`
* Get service by namespace `kubectl get services -n default`



### Helm

Install helm `brew install helm`
Added official repository `helm repo add stable https://charts.helm.sh/stable`
`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`
Update `helm repo update`
Prometheus install `helm install prometheus prometheus-community/prometheus`
Check prometheus `kubectl get pods -l app=prometheus-server`
Get all `kubectl get pods -n default`
Open interface prometheus `minikube service prometheus-server`


```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
```