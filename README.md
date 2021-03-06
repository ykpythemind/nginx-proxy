# nginx-proxy

Dockerfile for my VPS Server

* https://github.com/jwilder/nginx-proxy
* https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion

ref:
http://tech.quartetcom.co.jp/2017/04/11/multiple-ssl-apps-on-one-docker-host/

## usage

```
docker network create nginx-proxy
```

```
git clone https://github.com/ykpythemind/nginx-proxy
cd nginx-proxy
docker-compose up -d
```

---

in another repository

```
# ./docker-compose.yml
version: '3'
services:
  nginx:
    image: nginx
    # ports:
    # - "8080:80"
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
      name: nginx-proxy
```

Specify network 'nginx-proxy'
