# To Do App


```yaml
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
  ```

OR

  
git clone https://github.com/thobalose/todo-list-app.git ; cd todo-list-app/
npm install
node app.js

To build a docker image for the todo-list-app and run it inside a container execute

docker build -t thoba/todo-list-app .
The above with create an image with the latest tag. To run the container execute

docker run -it -p 8080:8080 --name todo_list_app thoba/todo-list-app

---


https://github.com/AdminTurnedDevOps/kubernetes-examples/tree/main/ingress-controller/minikube