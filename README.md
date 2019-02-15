# k8s-nginx
nginx in kubernetes

Prerequisite: Set up k8s cluster

### Deploy to k8s cluster:
```
kubectl apply -f nginx-deployment.yaml
kubectl get deployments
kubectl get pods -o wide
kubectl get replicasets -w
```
Try to remove one of the nginx docker containers, and like magic, k8s will automatically create a new one!

### Expose it as a service:
```
kubectl apply -f nginx-service.yaml
kubectl get services
kubectl describe service nginx-service
```
You should be able to curl it now

### Remove the resources
```
kubectl delete -f nginx-deployment.yaml
kubectl delete -f nginx-service.yaml
```

### Namespaces
```
kubectl apply -f namespace-example.yaml
kubectl get namespaces
```

#### Create a ResourceQuota object, limit running pods in namespace to 2
```
kubectl apply -f pod-quota.yaml --namespace=namespace-example
```

#### Deploy nginx with 3 pods into the namespaces
```
kubectl apply -f nginx-deployment.yaml --namespace=namespace-example
kubectl get deployment nginx-deployment --namespace=namespace-example
kubectl get deployment nginx-deployment --namespace=namespace-example --output=yaml
```
Only 2 replicas are allowed

#### Delete namespaces
```
kubectl delete -f namespace-example.yaml
```
