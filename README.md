# docker-nginx

Using `nginx-proxy` and `nginx-proxy-companion` with docker-compose.
- https://github.com/jwilder/nginx-proxy
- https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion

Create external network by: `sudo docker network create nginx-proxy`

Then simply: `sudo docker-compose up -d`

And add to your app docker-compose (i'm using v3.5):
```
networks:
  default:
    external:
      name: nginx-proxy
      
service:
   web[or-whatever-you-call-it]:
     expose["ports" will not suffice]:
      - PORT
     environment:
      - VIRTUAL_HOST=your.domain.com [add comma separated if more]
      - LETSENCRYPT_HOST=your.domain.com [add comma separated if more]
      - LETSENCRYPT_EMAIL=your.email.com
```
