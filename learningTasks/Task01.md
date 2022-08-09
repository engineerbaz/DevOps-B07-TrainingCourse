# Learning Tasks

## Task 1
Good Day!

Here is learning practice 

1. Pull any 5 Images from Registry (i.e ``` Nginx, Busybox, alpine or etc ```)
2. Run Busybox without pulling with printing output as *"Not Hello World"*
3. Run webserver on port 8087 named as your name + date (i.e ` BAZ09August `)
4. Run container with alpine and Delete Image.
5. Use image engineerbaz/hw with tag of v8 and run it on port of your choice.
6. Make & Kill Container name "MyContainerMyImage" 
7. Run following command in Docker 

Make a file named as ` Dockerfile ` and copy data as 

``` 
FROM ubuntu 
MAINTAINER BAZTechKnow 

RUN apt-get update 
RUN apt-get install –y nginx 
CMD [“echo”,”Image created”] 

```

Save the file and run command 
```
docker build -t ImageName:TagName .
```

Now see if Image is present by checking ` Docker Images `
