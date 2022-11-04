# RollingUpdates

```yaml

kind: Deployment
apiVersion: apps/v1
metadata:
    name: nginx-deployment
spec:
    replicas: 5
    strategy:
        type: RollingUpdate
        rollingUpdate:
# Allow up to seven pods to be running
# during the update process
            maxSurge: 2
# Require at least four pods to be running
# during the update process
            maxUnavailable: 1
    selector:
        matchLabels:
            app: nginx
    template:
        metadata:
            name: nginx
            labels:
                app: nginx
        spec:
            containers:
                - name: nginx
                  image: nginx:1.7.9


````

```yaml
kubectl apply -f deployment.yaml --record
kubectl rollout history deployment

kubectl rollout status deployment nginx-deployment
kubectl rollout history deployment nginx-deployment --revision=1
kubectl rollout undo deployment nginx-deployment --to-revision=1
```






========== OR ================

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: navbar-deployment
spec:
  selector:
    matchLabels:
      app: helloworld
  replicas: 3 # tells deployment to run 3 pods matching the template
  template: # create pods using pod definition in this template
    metadata:
      labels:
        app: helloworld
    spec:
      containers:
      - name: helloworld
        image: karthequian/helloworld:black
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: navbar-service
spec:
  # if your cluster supports it, uncomment the following to automatically create
  # an external load-balanced IP for the frontend service.
  type: NodePort
  ports:
  - port: 80
    protocol: TCP
    targetPort: 80
  selector:
    app: helloworld



````

```yaml
kubectl create -f helloworld-black.yaml --record
minikube service navbar-service
kubectl set image deployment/navbar-deployment helloworld=karthequian/helloworld:blue
kubectl rollout history deployment/navbar-deployment
kubectl rollout undo deployment/navbar-deployment



````