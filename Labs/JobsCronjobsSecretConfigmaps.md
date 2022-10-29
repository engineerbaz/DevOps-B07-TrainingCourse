## ENV 

Plain Key Value:
================

kubectl run nginx --image=nginx --env="Title=Hello from the environment";
kubectl run nginx --image=nginx --env "DEMO_GREETING=Hello from the environment";

kubectl exec -it nginx -- printenv

OR

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
  labels:
    purpose: demonstrate-envars
spec:
  containers:
  - name: nginx
    image: nginx
    env:
    - name: DEMO_GREETING
      value: "Hello from the environment"
    - name: DEMO_FAREWELL
      value: "Such a sweet sorrow"
```

`kubectl exec -it nginx -- printenv`


## Jobs

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: finalcountdown
spec:
  template:
    metadata:
      name: finalcountdown
    spec:
      containers:
      - name: counter
        image: busybox
        command:
         - bin/sh
         - -c
         - "for i in 9 8 7 6 5 4 3 2 1 ; do echo $i ; done"
      restartPolicy: Never #could also be Always or OnFailure

```
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data: 
  APP_COLOR: blue
  APP_MODE: prod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: simple-webapp-color
  labels:
    name: simple-webapp-color
spec:
  containers:
  - name: simple-webapp-color
    image: simple-webapp-color
    ports:
    - containerPort: 8080
    envFrom:
    - configMapRef
      name: app-config
```
  


## Secrets
$ echo -n "root" > ./username.txt
$ echo -n "password" > ./password.txt
$ kubectl create secret generic db-user-pass --from-file=./username.txt —from-file=./password.txt
 
 or 
 $ kubectl create secret generic ssl-certificate --from-file=ssh-privatekey=~/.ssh/id_rsa --ssl-cert-=ssl-cert=mysslcert.crt

secrets-db-secret.yml

```yaml 
apiVersion: v1
kind: Secret
metadata:
  name: db-secret
  type: Opaque
data:
  password: cm9vdA==
  username: cGFzc3dvcmQ=
  
  ```

$ echo -n "root" | base64
cm9vdA==
$ echo -n "password" | base64
cGFzc3dvcmQ=

After creating the yml file, you can use kubectl create:
$ kubectl create -f secrets-db-secret.yml

apiVersion: batch/v1
kind: Job
metadata:
  name: job-example
spec:
  backoffLimit: 4
  completions: 4
  parallelism: 2
  template:
    spec:
      containers:
      - name: hello
        image: alpine:latest
        command: ["/bin/sh", "-c"]
        args: ["echo hello from $HOSTNAME!"]
      restartPolicy: Never


## CronJob

apiVersion: batch/v1beta1
kind: CronJob
metadata:
 name: batch-job-every-minute
spec:
 schedule: "* * * * *"
 jobTemplate:
   spec:
     template:
       metadata:
         labels:
           app: periodic-batch-job
       spec:
         restartPolicy: OnFailure
         containers:
         - name: main
           image: docker/whalesay
           command: ["cowsay",  "This is a CronJob!"]