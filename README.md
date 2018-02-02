# nginx-proxy

Dockerfile for my VPS Server

- https://github.com/jwilder/nginx-proxy
- https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion

ref:
http://tech.quartetcom.co.jp/2017/04/11/multiple-ssl-apps-on-one-docker-host/

## usage

```
cd
git clone https://github.com/ykpythemind/nginx-proxy
cd nginx-proxy
docker-compose up -d
```

Docker creates `nginxproxy_default` network

---

in another repository

```
# ./docker-compose.yml
version: '2'
services:
  nginx:
    build: .
    # volumes:
    #  - .:/var/www
    environment:
      VIRTUAL_HOST: myapp.mydomain.com
      # VIRTUAL_PORT: 8080
      LETSENCRYPT_HOST: myapp.mydomain.com
      LETSENCRYPT_EMAIL: your.real@email.com
    restart: always
networks:
  default:
    external:
      name: nginxproxy_default
```
