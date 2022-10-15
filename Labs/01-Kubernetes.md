# Kubernetes


## Namespace
Let find out

## Pod 

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-1-nginx
  labels:
    app: myapp
    type: front-end
spec:
  containers:
   - name: nginx-container
     image: nginx
```

## ReplicaSet

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: replicaset-2-nginx # Replicaset Name
  labels:
    app: myapp-replicaset # replicaset Label
spec:
  template:
   metadata:
    name: myapp-pod # POD Name
    labels:
     app: pod-myapp # POD Label
   spec:
    containers:
     - name: nginx-container
       image: nginx
  replicas: 2
  selector:
    matchLabels:
      app: pod-myapp # POD Label


```


## Deployment 

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment-3-nginx # Deployment Name
  labels:
    app: myapp-deploy # Deployment Lable
spec:
  template:
   metadata:
    name: myapp-pod # POD Name
    labels:
     app: pod-myapp # POD LABEL
   spec:
    containers:
     - name: nginx-container
       image: nginx
  replicas: 2
  selector:
    matchLabels:
      app: pod-myapp # POD LABEL
```

```yaml
kubectl run pod-1-nginx-1 --image=nginx
kubectl create deployment deployment-2-nginx-2 --image=nginx
kubectl scale deployment deployment-2-nginx-2 --replicas=3
```
 