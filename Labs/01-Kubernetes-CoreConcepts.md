# Core Concept

Imperative Commands

`kubectl create deployment nginx --image nginx`

Imperative Object Configuration

```yaml
kubectl create -f nginx.yaml
kubectl delete -f nginx.yaml -f redis.yaml
kubectl replace -f nginx.yaml
```

Declarative Object Configuration

`kubectl apply -f configs/`


```yaml
kubectl api-resources
kubectl api-versions
kubectl explain
kubectl explain --recursive
kubectl cluster-info
kubectl <command> --help
```


