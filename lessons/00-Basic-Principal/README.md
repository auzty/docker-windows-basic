# Basic Principal of Docker

# Goals 

- User understand what is Docker Images ,what is Docker Containers and Docker Registry Repository
- User can run Docker Containers from public docker registry repository
- User can bind port to running containers
- User can Enter to tty1 or container shell

## What Is Docker ? 

Docker is a set of platform as a service products that use OS-level virtualization. There are two main base concept that must be clearly understand.
1. Docker Image 
    Docker Image is a base software or you can called it an OS of the container. For Example : `ubuntu:focal` Images, are base component that using `Ubuntu` with codename `focal` (Ubuntu 20.04.4 LTS Focal Fossa). 

    How we can get Docker Images? there are three method that wew can get the Docker Images:
        - Pulling public repository of docker images. i.e., https://hub.docker.com/search?q=&image_filter=official
        - Building your own `Docker Image` using `build` command
        - Commiting running container as new Image using `docker commit`
2. Docker Containers
    Docker Containers is a running instance from Docker Images. How to create a containers? there are two ways to create it:
        - using `docker run` command
        - using `docker-compose` command
    How to start a stopped container? just using `docker start containername` or run again using `docker-compose`
    more command about container can be found on this link https://docs.docker.com/engine/reference/commandline/run/