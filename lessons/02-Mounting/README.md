# Make it Persistent

# Goals

- User can make the config / data persistent (when container get destroyed or recreated)

## The Concept

Usually we need persistency on our data, for example running a postgres container, that contain database. when we just docker run it, the postgres data will be available as local volume inside the container. So when we destroy the container, our data will be gone. So we need persistency of the data / files sometimes.

## Mounting the data

Docker have a command that provide the persistency data 
1. using host (laptop/pc) folder and mount it inside the container
2. using docker volume (created on docker and the container just call it volume to use it)

### Using host volume

By adding `-v` command when run a container, we can mount host folder to inside container, for example, we want to mount html folder to htdocs inside the container (this still using our custom image httpd or official http are ok too)
> docker run --rm -p --name httpd-test 8000:80 -v `pwd`/html:/usr/local/apache2/htdocs httpd:alpine
The command `pwd` are 