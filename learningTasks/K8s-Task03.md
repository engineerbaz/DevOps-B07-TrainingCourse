# Kubernetes Task 03 

Learning task

- Create a namespace called k8-lab1 in your cluster.
- Run the following pods in this namespace.
  - A pod called pod-a with a single container running the nginx image.
  - A pod called pod-b that has one container running the image redis:alpine, and one container running nginx:alpine. 
- Write down the output of `kubectl get pods` for the kube-system namespace.
- Delete the namespace

### Task 2

- Create a namespace k8-lab2
- Create a file called deploy.yaml that declares a deployment with name nginx-deploy in the recetly created namespace, with three replicas running the nginx:1.16 image. Each pod should have the label app=revproxy. The deployment can have the label client=user.
- Create a new Deployment in the namespace with the below attributes using your own deployment definition file: `Name: httpd-fe; Replicas: 3; Image: httpd:2.4-alpine`
- Delete the namespace created in the first step

### Task 3

- Create all the resources in the cka-lab6 ns and delete the ns after completion.
(optional) 
- How many Services exist on the system? and Check the Default kubernetes service and find out its service type
- Identify the target port of the default kubernetes service 
- Identify the labels on the default kubernetes service
- How many Endpoints are attached on the 'kubernetes' service?

- Create a deployment deploy-webapp using image `engineerbaz/htmlfile:5` having 3 replicas
- Create a service using the following parameters : `Name: service-webapp; Type: NodePort; targetPort: 80; port: 80; nodePort: 30080; selector: simple-webapp` and Try to access the deployment using Node IP and port 30080

- Create a new deployment called deploy-02 in the dev-ns namespace with 2 containers using images nginx & httpd images & expose them. It should have 2 replicas and they should b eexposed so both webpage can be reachable 


