# Kubernetes
API Primitives LAB - YAML 

## Namespace

```yaml
apiVersion: v1
kind: Namespace
metadata:
 name: devtest
 ```
`kubectl get namespace`

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
 
## Services 

```yaml
kubectl run nginx --image=nginx
kubectl expose pod nginx --port 80
```
`curl cluster_IP.141:80`

`kubectl edit service nginx` type: NodePort

```yaml 
kubectl get node -o wide
kubectl get all -o wide
```

On Browser >>> INTERNAL_IP:Port(NodePort)
example >>> http://172.16.16.100:32732/



