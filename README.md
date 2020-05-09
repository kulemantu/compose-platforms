# Proxy-enabled open source platforms via Docker-Compose
Configure the `*.env.example` files and rename to `*.env` files
**Note:** Not all `docker-compose.yml` files read from `*.env `files 

## Set up domains pointing to platforms using Nginx-proxy
Create `nginx-proxy` network to containers to be exposed via port `80`/`443`
```
docker network create nginx-proxy
```

Run `docker-compose up -d` from the `nginx-proxy` folder and ensure that ports `80` and `443` are bindable.
```
cd nginx-proxy
docker-compose up -d
docker-compose -f # To see added services and HTTP requests log
```

Point domains to your instances and generate SSL certificates with LetsEncrypt by
- Setting env `VIRTUAL_HOST` and `LETSENCRYPT_HOST` to "subdomain.example.com" or "example.com"
- Setting env `VIRTUAL_PORT` to the exposed port for your app service in the `docker-compose.yml` files
- Setting env `DEFAULT_EMAIL` in the `nging-proxy/nginx-proxy-letsencrypt` service for your support account

Credit
- https://github.com/nginx-proxy/nginx-proxy
- https://github.com/nginx-proxy/docker-letsencrypt-nginx-proxy-companion

### Portainer
Browser-based monitoring for single or multiple Docker installations

Credit
- https://github.com/portainer/portainer

### Botpress
Studio-style chatbot design and configuration

Credit
- https://github.com/botpress/botpress

### Directus 
Headless CMS that maps to raw MySQL structure

Credit
- https://github.com/directus/directus

# Contributing
