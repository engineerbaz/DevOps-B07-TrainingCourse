# Kubernetes Wordsmith Demo

Wordsmith is the demo project shown at DockerCon EU 2017 and 2018.

The demo app runs across three containers:

**db** - a Postgres database which stores words

**words** - a Java REST API which serves words read from the database

**web** - a Go web application which calls the API and builds words into sentences:



```yaml
# Word -- Web
apiVersion: v1
kind: Service
metadata:
  name: db
  labels:
    app: words-db
spec:
  ports:
    - port: 5432
      targetPort: 5432
      name: db
  selector:
    app: words-db
  clusterIP: None
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: db
  labels:
    app: words-db
spec:
  selector:
    matchLabels:
      app: words-db
  template:
    metadata:
      labels:
        app: words-db
    spec:
      containers:
      - name: db
        image: dockersamples/k8s-wordsmith-db
        ports:
        - containerPort: 5432
          name: db
---
apiVersion: v1
kind: Service
metadata:
  name: words
  labels:
    app: words-api
spec:
  ports:
    - port: 8080
      targetPort: 8080
      name: api
  selector:
    app: words-api
  clusterIP: None
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: words
  labels:
    app: words-api
spec:
  replicas: 5
  selector:
    matchLabels:
      app: words-api
  template:
    metadata:
      labels:
        app: words-api
    spec:
      containers:
      - name: words
        image: dockersamples/k8s-wordsmith-api
        ports:
        - containerPort: 8080
          name: api
---
apiVersion: v1
kind: Service
metadata:
  name: web
  labels:
    app: words-web
spec:
  ports:
    - port: 8081
      targetPort: 80
      name: web
  selector:
    app: words-web
  type: LoadBalancer
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
  labels:
    app: words-web
spec:
  selector:
    matchLabels:
      app: words-web
  template:
    metadata:
      labels:
        app: words-web
    spec:
      containers:
      - name: web
        image: dockersamples/k8s-wordsmith-web
        ports:
        - containerPort: 80
          name: words-web


```

THe end 


----


this is new file 

