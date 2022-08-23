# Learning Tasks

## Task 2
*Good Day!* 

Here are some tasks for your learning & practice , You can complete and share working (snapshot or in text file) in Classmaker.

Task 1 to 6 are *Must*, while 7 & 8 are optional

1. Make Dockerfile for any of well-known image (i.e ``` Nginx, Busybox, alpine or etc ```)
2. Make a cutomized Image for ping your IP 
3. Create a image of webpage of your choice ( you may upload on Dockerhub)
4. Create 2 Network of Bridge Type named as `nw01` and `nw02`
5. Make two different containers in two networks 
6. 
7.  
8.    
9.  Use image engineerbaz/hw with tag of v8 and run it on port of your choice.
10. Run following command in Docker 

Make a file named as ` Dockerfile ` and copy data as 

``` 
FROM nginx:latest
MAINTAINER BAZTechKnow 
COPY . /usr/share/nginx/html
# comment
ENV abc=hello

```

Save the file and run command 
```
docker build -t ImageName:TagName .
```

Now see if Image is present by checking ` Docker Images `
