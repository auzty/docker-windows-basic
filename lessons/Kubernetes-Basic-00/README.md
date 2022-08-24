# Kubernetes Basic

## Installation

on docker desktop, just enable the kubernetes cluster on settings.

![kubernetes](../../readme-resources/enable-kubernetes.jpg)

# Goals

- User can deploy and access the deployment on localhost

## The Concept

Kubernetes are system for automating deployment, scaling, and management of containerized applications. In short, Kubernetes (k8s) are container management. 

## Some Kubernetes Terminology

### POD

pod are smallest component (a running container). So if deploying a pod, that will be have a One main containers

### DEPLOYMENT 

deployment are deploying multiple pod to one deployment (sometimes like deploying an main app with daemon, that need 1 pod for main app, and 1 pod for daemon. because docker best practice are one app per container). when we are using deployment, the kubernetes can assure that the service always running, if the pod deleted, it will recreate pod and running that pod again based on our configuration

### SERVICE

service are how to exposing our deployment / pod to external or internal access. because we cannot access the pod / deployment when we didn't create a service and expose it

### Other Stuff

on kubernetes also have a `volumes` like docker containers, but there are many method that can be implemented, we will implement basic volume later

## Deploying first app

make sure the kubernetes are enabled 

**kubectl** are kubernetes cli command

> kubectl version --short

deploying an nginx 

this is will be pull an nginx docker images from dockerhub and deploy it to kubernetes cluster

> kubectl create deployment nginx --image=nginx

expose nginx deployment

> kubectl create service nodeport nginx --tcp=80:80

and then check the exposing port using 

> kubectl get service

and access it from your localhost

![nginx](../../readme-resources/kubernetes-svc-nginx.jpg)


## Command Notes

1. `kubectl create deployment deploymentname `
    this is will create a deployment with name `deploymentname`
2. `kubectl create service nodeport nginx --tcp=80:80`
    this is will create a service and expose it to kubernetes node
3. `kubectl get pod`
    will print a pod list
4. `kubectl get deployment` / `kubectl get deploy`
    will print a deployment list
5. `kubectl get service` / `kubectl get svc`
    will print a list of service 
6. `kubectl delete service svcname`
    will delete service with name `svcname`
7. `kubectl delete pod podname`
    will delete a pod with name `podname`
8. `kubectl delete deploy deploymentname`
    will delete a deployment with name `deploymentname`

and there are many others command that can be found on their official documentations https://kubernetes.io/docs/concepts/ 