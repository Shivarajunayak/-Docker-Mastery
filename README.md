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

### Display version & 
```
docker --version  
```

### Displays the kernel version, number of containers and docker info   images etc...
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

### Exit from container shell type exit
``` exit ```

Press ```ctrl+PQ ``` to run container image in background.

### Listing Docker Container
```docker ps ```  or ``` docker container ls```

### Run back the container shell 
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


<b>The process of taking an application and configuring it to
run as a container is called “containerizing”. Sometimes
we call it “Dockerizing” </b>
### Containerization process for an app:

<b>1.</b> Start with your application code
<b>2.</b> Create a Dockerfile that describes your app, its dependencies, and how to run it
<b>3.</b> Feed this Dockerfile into the docker image build
command to create an image
<b>4.</b> Create and run a container from that image