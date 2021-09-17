# Docker-Mastery


## Some Basic Docker Commands


### Installing Docker CE in Ubnutu
Apt Package index will be updated
```
 sudo apt-get update 
```
Install Docker CE and Containerd - Latest Version
```
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

### Display version 
```
docker --version  
```

### Displays the kernel version, number of containers and docker info   images etc... or Simply Docker is running or not
```
docker info  
```

### Command to check if client and server is working
```
docker version
```
###  Pulling images from Repository
```
docker image pull <repository>:<tag>
```
<b>For example</b>: 
```
docker image pull nginx:latest
```
<b> Two important thing to remember </b>
1. If you do not specify an image tag after the repository name, Docker will assume you are referring to the image tagged as latest
2. The latest tag doesn’t have any magical powers! Just because an image is tagged as latest does not guarantee it is the most recent image in a repository!

You can also use ``` docker pull alpine:latest ``` instead of ``` docker image pull alpine:latest ```

### Listing Images
```docker image ls ``` or ``` docker images```

### Removing Image
```docker container rm alpine:latest ```

To confirm if it is deleted you can use ``` docker image ls```

### Docker Container
A container is the runtime instance of an image.

<b>Run a container from an image in an interactive mode </b>
```
 docker run -it <user name>/helloworld sh
```


### Exit the container without terminating it
``` exit ```

Press ```ctrl+PQ ``` to run container image in background.

### Listing Docker Container
```docker ps ```  or ``` docker container ls```

### Attaching shell to the container that are running in background 
```docker exec -it <uniq name or id> sh ```

### Stop container
```docker container stop <uniq name or id>  ```

### Listing container that are running in the background
```docker container ls -a``` or ```docker ps -a```

### Restart the stopped container
```  docker container start <uniq name or id> ```

<i><b>Note</b>: Stopping a container does not destroy you data inside file system of container </i>

### Remove container permanently
``` docker container rm <container uniq name or id>```

<i><b>Note</b>: Removing container will now permanently delete files inside container filesystem</i>

### Renaming the container
``` docker run -d --name mycontainer <repo name>/helloworld ```

### Accessing the running container in browser
``` docker run -d --name mycontainer -p 8100:80 <repo name>/helloworld```

<i><b>Note</b>: write ```localhost:8100``` in your browser now to see the output</i>

### Containerization
<i>The process of taking an application and configuring it to run as a container is called “containerizing”. Sometimes we call it “Dockerizing” </i>

### Containerization process for an app:
<b>1.</b> Start with your application code
<b>2.</b> Create a Dockerfile that describes your app, its dependencies, and how to run it
<b>3.</b> Feed this Dockerfile into the docker image build
command to create an image
<b>4.</b> Create and run a container from that image

### Docker File
It is a simple text file with instructions on how to build your images.
<b>Purpose:</b>:
1. To describe the application
2. To tell Docker how to containerize the application (create an image with the app inside)

<i><b>Note</b>: Docker file cannot be reverse engineered from any image</i>

### PUSHING IMAGES
Its main advantage is portability which means you can use it from anywhere in the world.
1. First you have to save your image to registry like docker hub
2. So, for that you need to sign up for the account first at https://hub.docker.com

<i><b>Note</b>: One thing important to know is for pushing an image to docker hub, we need our images to be built as ```username/repository:tag```
</i>

Previously we created image with ```docker build -t first-docker-app .``` which does not include username.

So, now we have 2 options:

1. Either we create image from same Docker file  
```image docker build -t <username>/first-docker-app .```
2. Or we  use docker tag command which could help us in making a new image from existing image with different name tags
```docker tag first-docker-app <username>/first-docker-app```

<b>Now we can publish our image to Docker Hub registry.</b>
```docker push <username>/first-docker-app ```

<i>Now we can pull our image using docker pull from anywhere in the world and deploy with docker run command. </i>

## Inspect the Docker Image
<b> It is also a great way to inspect layers in image</b>
To inspect the layer of the image 
```docker history <image name>```
And
```docker inspect <image name>```

``` docker image insepct <image name>:<tag>```
or
``` docker image pull <repo name>:<tag>```

## View the image hash code/ digest of an image
``` docker image ls --digests <image name>```
For example
``` docker image ls --digests alpine```

## Pulling an image with digests
First remove the previous image (note its digests)
```docker image rm alpine:latest ```
Now,
```docker image pull alpine@sha256:c0537...7c0a7726c88e2bb7584dc96```

## Delete all the images at once
It will list all the images unique id
``` docker image ls -q  ```
Now, you can delete all the images with their id
```docker image rm $(docker imag ls -q) -f ```