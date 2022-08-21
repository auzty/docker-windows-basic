# Building Your Own Docker Images 

# Goals

- User can create custom docker images
- User can push it to public repository

## The Concept

Sometimes, you need to create your own docker images for your specific purpose. I.e., you want to display other html output from `httpd:alpine`, you can modify it from the base images.

# Creating Custom Images

Docker have format that must be followed for creating an images, all available command can be found on https://docs.docker.com/engine/reference/builder/#format

For Example there are `Dockerfile` that contain

```
# this is a base images that we want to modify
FROM httpd:alpine

# ADD / COPY command will copy . (current directory) to /usr/local/apache2/htdocs
ADD . /usr/local/apache2/htdocs

# default command to run foreground
CMD ["httpd-foreground"]
```

*notes* : 

How we know what corrent directory for copying the file? (in this example we copying `index.html` to `/usr/local/apache2/htdocs`) ? 
- you can docker run first
- `docker exec -it httpd-test /bin/sh` and check the config using `cat` or `vi` , `cat /usr/local/apache2/conf/httpd.conf` and find the `DocumentRoot` section. 

We need to know about the images that we want to modify. and we can search about that on dockerhub repo from that official `httpd` images ( https://hub.docker.com/_/httpd )

To build the first custom images , you can just run command: 
> docker build -t imagename:tagname .
the imagename is required, the tagname are optional, and the default is `latest` , 

you can run and check after the build,
> docker run --rm -p 8000:80 imagename:tagname

The localhost:8000 should said `Hello There` instead `It works!` (default)

## Important Part on Building Docker Images

- Docker Images command should be running as foreground (not background), the `httpd-foreground` are scritp that will run `httpd` service on foreground. you can check the script on their official repo https://github.com/docker-library/httpd/blob/f3b7fd9c8ef59d1ad46c8b2a27df3e02d822834f/2.4/alpine/httpd-foreground
- If Docker Images command are background service, the container will be stopped immediately after running.
  > docker run --rm -p 8000:80 imagename:tagname echo hello
  the command above will run one time, displaying `hello` and then the container will stopped
- There are only one process per container (best practices), but if need more that one process, other software are needed http://supervisord.org/ (that will not cover in this repo)

# Pushing Docker Image

After building an images, and to distribute the images to other server, we need to push our images to registry repository ( you can create your own registry, or using public dockerhub registry or other)

you can go to dockerhub and register https://hub.docker.com/signup

The Image name format must be followed by the username, i.e., my username are `auzty`, so the custom images should be `auzty/imagename:tagname` and then you can push it using docker command
> docker push auzty/imagename:tagname

and then on the other server just need pull that images
> docker pull auzty/imagename:tagname