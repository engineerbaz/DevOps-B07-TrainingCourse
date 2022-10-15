# Kubernetes Task 03 

Learning task

- Create a namespace called k8-lab1 in your cluster.
- Run the following pods in this namespace.
  - A pod called pod-a with a single container running the nginx image.
  - A pod called pod-b that has one container running the image redis:alpine, and one container running nginx:alpine. 
- Write down the output of `kubectl get pods` for the kube-system namespace.
- Delete the namespace

task 2


- Create a namespace k8-lab2
- Create a file called deploy.yaml that declares a deployment with name nginx-deploy in the recetly created namespace, with three replicas running the nginx:1.16 image. Each pod should have the label app=revproxy. The deployment can have the label client=user.
- Create a new Deployment in the namespace with the below attributes using your own deployment definition file: `Name: httpd-fe; Replicas: 3; Image: httpd:2.4-alpine`
- Delete the namespace created in the first step

