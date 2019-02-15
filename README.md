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
