# Docker-Mastery


## Some Basic Docker Commands


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