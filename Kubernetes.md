# Kubernetes Complete Guide

## Setting Up Kubernetes
```sh
# Check if kubectl is installed
kubectl version --client

# Install Minikube (Local Kubernetes Cluster)
# macOS
brew install minikube
# Ubuntu/Debian
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && \
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Windows (Using Chocolatey)
choco install minikube
```

## Starting Minikube
```sh
minikube start
```

## Checking Cluster Status
```sh
kubectl cluster-info
kubectl get nodes
```

## Creating a Pod
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: nginx
```
```sh
kubectl apply -f pod.yaml
kubectl get pods
```

## Creating a Deployment
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: nginx
```
```sh
kubectl apply -f deployment.yaml
kubectl get deployments
```

## Scaling a Deployment
```sh
kubectl scale deployment my-deployment --replicas=3
kubectl get pods
```

## Exposing a Deployment
```sh
kubectl expose deployment my-deployment --type=NodePort --port=80
kubectl get services
```

## Viewing Logs
```sh
kubectl logs my-pod
```

## Executing Commands in a Pod
```sh
kubectl exec -it my-pod -- /bin/sh
```

## Deleting Resources
```sh
kubectl delete pod my-pod
kubectl delete deployment my-deployment
kubectl delete service my-deployment
```

## Checking Resource Usage
```sh
kubectl top pods
kubectl top nodes
```

This guide covers essential Kubernetes concepts and commands.

