# Learning Tasks

## Task 2
*Good Day!* 

Here are some tasks for your learning & practice , You can complete and share working (snapshot or in text file) in Classmaker.

Task 1 to 7 are *Must*, while 8 & 9 are optional

1. Make Dockerfile for any of well-known image (i.e ``` Nginx, Busybox, alpine or etc ```)
2. Make a cutomized Image for pinging your IP 
3. Create a image of webpage of your choice ( you may upload on Dockerhub)
4. Create 2 Network of Bridge Type named as `nw01` and `nw02`
5. Make two different containers in two networks 
6. Using image from _engineerbaz/dockerlabs_ create a container to show output
7. Create a Volume and store current date from _conatainer01_ and access from _container02_  
8. Get data from https://github.com/engineerbaz/DevOps-B07-TrainingCourse/blob/main/learningTasks/project-todoList.md and run as project
9. Run following command in Docker 

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
