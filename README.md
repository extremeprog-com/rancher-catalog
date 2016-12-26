# rancher-catalog
Rancher-based catalog of extremeprog services.

## Contents

### Git Proxy 
Easy access to private repos for automation services. Repo https://github.com/extremeprog-com/git-proxy.

#### Usage
Adding cattle from private repo. Go to **Settings -> Catalog -> Add Catalog**.
Add catalog with url `http://proxy.git-proxy/git@github.com:yourproject/Project.git#${BRANCH_NAME}`. 

Adding build from private repo (in **docker-compose.yml**):
```yml
yourproject:
    build: http://proxy.git-proxy/git@github.com:yourproject/Project.git#${BRANCH_NAME}
```

### Heaven
Nginx container with LetsEncrypt SSL support for simple and fast Docker deployments. Repo https://github.com/extremeprog-com/heaven.

#### Usage

Add to `docker-compose.yml`.

```
heaven-backend:
  image: rancher/dns-service
  links:
  - just
```

And to your container service declaration a label

```
your-service:
  labels:
    io.rancher.scheduler.affinity:host_label_soft: heaven=1
```

### Just
A convenient tool for fast prototyping of web and mobile applications. Repo https://github.com/extremeprog-com/just.
