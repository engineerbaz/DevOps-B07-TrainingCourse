# Learning Tasks

## Task 1
*Good Day!*

Here are some tasks for your learning & practice , You can complete and share working (snapshot or in text file).

Task 1 to 6 are *Must*, while 7 & 8 are optional

1. Pull any 5 Images from Registry (i.e ``` Nginx, Busybox, alpine or etc ```)
2. Run Busybox without pulling with printing output as *"Not Hello World"*
3. Run webserver on port 8087 named as your name + date (i.e ` BAZ09August `)
4. Run container with alpine and Delete Image.
5. Use image engineerbaz/hw with tag of v8 and run it on port of your choice.
6. Make & Kill Container name *"MyContainerMyImage"* 
7. Create 3 Containers of Ubuntu and ping IP of each ones
8. Run following command in Docker 

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
