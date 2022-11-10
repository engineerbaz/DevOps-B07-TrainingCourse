# volumes

## Volume with two containers

**1. Simple Volume using emptyDir**

```yaml
kind: Pod
apiVersion: v1
metadata:
  name: myvol
  labels:
    app: myapp
spec:
  volumes:
  - name: share-dir
    emptyDir: {}
  containers:
  - name: container-one
    image: alpine
    volumeMounts:
    - name: share-dir
      mountPath: /var/cont-one
  - name: container-two
    image: nginx
    ports:
    - containerPort: 80
    volumeMounts:
    - name: share-dir
      mountPath: /var/cont-two
  restartPolicy: Never
```

**- Two Containers with Volume (Webserver and linux container)**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: volume-example
spec:
  containers:
  - name: nginx
    image: nginx:stable-alpine
    volumeMounts:
    - name: html
      mountPath: /usr/share/nginx/html
      ReadOnly: true
  - name: content
    image: alpine:latest
    command: ["/bin/sh", "-c"]
    args:
      - while true; do
         date >> /html/index.html;
         sleep 5;
      done
    volumeMounts:
    - name: html
      mountPath: /html
  volumes:
  - name: html
    emptyDir: {}
```


```yaml 
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv
spec:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 100M
  hostPath:
    path: /tmp/pv
  storageClassName: abc
  persistentVolumeReclaimPolicy: Delete  # can be Recycle or Retain (retain is default)

--

apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 50M
  storageClassName: abc

--

apiVersion: v1
kind: Pod
metadata:
  name: pod-pv
spec:
  volumes:
  - name: pvol
    persistentVolumeClaim:
      claimName: pvc
  containers:
  - image: nginx
    name: cont-one
    volumeMounts:
    - name: pvol
      mountPath: /tmp/pv
    imagePullPolicy: IfNotPresent
  restartPolicy: Never
```


