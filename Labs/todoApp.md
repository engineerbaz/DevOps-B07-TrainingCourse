apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: todo-app
  name: todo-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: todo-app
  template:
    metadata:
      labels:
        app: todo-app
    spec:
      containers:
      - image: thoba/todo-list-app
        name: todo-app
        ports:
        - containerPort: 8080

---
apiVersion: v1
# Indicates this as a service
kind: Service
metadata:
  # Service name
  name: todo-app
spec:
  selector:
    # Selector for Pods
    app: todo-app
  ports:
    # Port Map
  - port: 80
    targetPort: 8080
    protocol: TCP
  type: LoadBalancer