# Jenkins on Kubernetes using Minikube

### Setup

1. Create a minikube profile
```shell
# create
minikube start -p jenkins-minikube

# set as default profile
minikube profile jenkins-minikube
```
> Optionally `minikube start -p minikube-jenkins --memory 8192 --cpus 2`

2. Create a namespace
```shell
kubeclt create namespace jenkins
kubens jenkins
```

3. Deploy Kubernetes manifests
```shell
kubectl apply -f ./kubernetes
```