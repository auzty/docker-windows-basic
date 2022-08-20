# Basic Principal of Docker

# Goals 

- User understand what is Docker Images and what is Docker Containers and Docker Registry Repository
- User can run Docker Containers from public docker registry repository
- User can bind port to running containers
- User can Enter to tty1 or container shell

# 1

Docker is a set of platform as a service products that use OS-level virtualization. There are two main base concept that must be clearly understand.
1. Docker Image 
    Docker Image is a base software or you can called it an OS of the container. For Example : `ubuntu:focal` Images, are base component that using `Ubuntu` with codename `focal` (Ubuntu 20.04.4 LTS Focal Fossa). 
2. Docker Containers