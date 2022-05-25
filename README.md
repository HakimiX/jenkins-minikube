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