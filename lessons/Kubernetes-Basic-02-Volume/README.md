# Persistent Data with Volume

# Goal 

- user can use persistent volume to avoid data loss

## The Concept

Kubernetes have many volume plugins that can be configured internally or external. We will try the simplest volume that called `hostPath`, the concept are similar with docker volume mounting with `-v src:dest` 

## How to Deploy

remove the existing deployment (because i'm using same nginx name for `deployment` and `service`)

> kubectl delete -f deploy-nginx-full.yaml

and then create new deployment

> kubectl apply -f deploy-nginx-full.yaml

and then copy `index.html` to your windows path `C:/Users/theau/Projects/samplepersistent` and access the `localhost:30003` that will be displaying the `index.html` content


### Yaml Description

```yaml
      containers:
      - image: nginx
        imagePullPolicy: Always
        name: nginx
        volumeMounts:
        - mountPath: /usr/share/nginx/html #the mountpath inside the pod
          name: nginxvolume #name of volume (any name)
```
how to we know `/usr/share/nginx/html` ? you can explore on dockerhub (usually official nginx container will be using that directory by default)

---

```yaml
      securityContext: {}
      volumes:
      - hostPath: # this is type of kubernetes volume
          path: /run/desktop/mnt/host/c/Users/theau/Projects/samplepersistent 
          type: DirectoryOrCreate
        name: nginxvolume # this name must be match with pod volume name above
```

`path` are specific for windows docker-desktop app, the prefix are `/run/desktop/mnt/host/` andthen `c` for drive `C:/` and so on
