# Final Task
 
*Good Day!* 

Here are some tasks for your learning & practice , You can complete and share working (snapshot or in text file) in Classmaker.

Task 1 to 7 are *Must*, while 8 & 9 are optional

1. Run two Docker Containers using different menthods. 
2. Make Dockerfile for any 2 of well-known image (i.e ``` Nginx, Busybox, alpine or etc ```)
3. Make a cutomized Image for pinging IP (8.8.8.8) 
4. Create 2 Network of Bridge Type named as `nw01` and `nw02` and communicate containers on both of them 
5.   
6. Create  
7.  
8.  Using image from _engineerbaz/dockerlabs_ create a container to show output
9. Create a Volume and store current date from _conatainer01_ and access from _container02_  
10. Get data from https://github.com/engineerbaz/DevOps-B07-TrainingCourse/blob/main/learningTasks/project-todoList.md and run as project
11. Run following command in Docker 

Make a file named as ` Dockerfile ` and copy data as 

``` 
# Using official ubuntu image as a parent image
FROM ubuntu:latest

RUN apt-cache search nginx
RUN apt-get upda
te && apt-get install curl -y && apt-get install -y nginx
CMD ["nginx", "-g", "daemon off;"]

```

Save the file and run command 
```
docker build -t ImageName:TagName .
```

Now see if Image is present by checking ` Docker Images `  and run container.
