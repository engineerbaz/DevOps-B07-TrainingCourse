

1- Create atleast 2 resources in the "lab6" ns and delete after completion.

2- Create a deployment deploy-webapp using image `engineerbaz/htmlfile:5` having 3 replicas

3- Create a service using the following parameters : `Name: service-webapp; Type: NodePort; targetPort: 80; port: 80; nodePort: 30080; selector: simple-webapp` and Try to access the deployment using Node IP and port 30080

4- Create a new deployment called deploy-02 in the dev-ns namespace with 2 containers using images nginx & httpd images & expose them. It should have 2 replicas and they should be exposed so both webpages can be reachable 