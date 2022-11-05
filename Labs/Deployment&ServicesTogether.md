



### App 1

```yaml 

kind: Deployment
apiVersion: apps/v1
metadata:
  name: hostname-101-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: hostname
      version: v101
  template:
    metadata:
      labels:
        app: hostname
        version: v101
    spec:
      containers:
        - name: nginx-hostname
          image: kubegoldenguide/nginx-hostname:1.0.1
          ports:
            - containerPort: 80



```



### App 02 


```yaml 

kind: Deployment
apiVersion: apps/v1
metadata:
  name: hostname-102-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hostname
      version: v102
  template:
    metadata:
      labels:
        app: hostname
        version: v102
    spec:
      containers:
        - name: nginx-hostname
          image: kubegoldenguide/nginx-hostname:1.0.2
          ports:
            - containerPort: 80

```


### Service
Expose both deployments through a single service!

```yaml
kind: Service
apiVersion: v1
metadata:
  name: hostname-service
spec:
  selector:
    app: hostname
  type: NodePort
  ports:
    - port: 8080
      targetPort: 80

```

kubectl apply -f deploy.yaml 
kubectl apply -f service.yaml 

kubectl  get pod -o wide
kubectl get node -o wide

curl http://172.30.1.2:31543
curl http://172.30.2.2:31543

IPADDR=$(kubectl get pod hostname-101-deployment-685dd5865b-6b46v -o jsonpath={.status.podIP})


====

apiVersion: v1
kind: Pod
metadata:
  name: nginx-with-git
spec:
  volumes:
  - name: www
  containers:
  - name: nginx
    image: nginx
    volumeMounts:
    - name: www
      mountPath: /usr/share/nginx/html/
  - name: git
    image: alpine
    command: [ "sh", "-c", "apk add git && git clone https://github.com/octocat/Spoon-Knife /www" ]
    volumeMounts:
    - name: www
      mountPath: /www/
  restartPolicy: OnFailure


## Init container
apiVersion: v1
kind: Pod
metadata:
  name: nginx-with-init
spec:
  volumes:
  - name: www
  containers:
  - name: nginx
    image: nginx
    volumeMounts:
    - name: www
      mountPath: /usr/share/nginx/html/
  initContainers:
  - name: git
    image: alpine
    command: [ "sh", "-c", "apk add git && git clone https://github.com/octocat/Spoon-Knife /www" ]
    volumeMounts:
    - name: www
      mountPath: /www/

      