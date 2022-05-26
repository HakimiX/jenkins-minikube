# Jenkins on Kubernetes using Minikube

* [Setup](#setup)
* [Jenkins Data](#jenkins-data)

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

4. Navigate to jenkins using the minikube IP and service port 
```shell
# minikube ip 
minikube profile list

|------------------|-----------|---------|--------------|------|---------|---------|-------|
|     Profile      | VM Driver | Runtime |      IP      | Port | Version | Status  | Nodes |
|------------------|-----------|---------|--------------|------|---------|---------|-------|
| minikube         | hyperkit  | docker  | 192.168.64.2 | 8443 | v1.23.3 | Running |     1 |
| minikube-jenkins | hyperkit  | docker  | 192.168.64.7 | 8443 | v1.23.3 | Running |     1 |
|------------------|-----------|---------|--------------|------|---------|---------|-------|

# service port 
kubectl get service

NAME      TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)                                       AGE
jenkins   NodePort   10.108.176.124   <none>        8080:30408/TCP,50000:30707/TCP,80:30962/TCP   34m

# Navigate to 
http://192.168.64.7:30408
```

### Jenkins Data

The Jenkins data is stored in the minikube node, and can be accessed with SSH
![](resources/images/minikube-ssh.png)

