# Heaven
Nginx container with LetsEncrypt SSL for simple Docker deployments.

### Inspiration
https://www.youtube.com/watch?v=JxPj3GAYYZ0 https://www.youtube.com/watch?v=oW_7XBrDBAA

### Use Cases

- You have containers app1, app2, app-clap, ... You want them to be available as `http(s)://app1.yourdomain.com`, `http(s)://app2.yourdomain.com`, `http(s)://app-clap.yourdomain.com`...

- You have a developer with nick "mr-twister", ... He develops applications app1, app2, app-clap, and you want them to be available as `http(s)://app1.mr-twister.yourdomain.com`, `http(s)://app2.mr-twister.yourdomain.com`, `http(s)://app-clap.mr-twister.yourdomain.com`...

- You want to have a payment-free LetsEncrypt SSL for `https://` support. You dont't have to setup anything – it's fully automated!

- You want to use the same behaviour with Rancher (fully automated), Swarm, ...

### Usage

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