# compose_stream

This docker-compose provides a reverse proxy Traefik, a Web server Nginx with FlowPlayer embeded, and a Nginx Streaming server.

## Testing it in local

First step, add the following lines into your /etc/hosts file to get something like this :
```
sudo vim /etc/hosts
```
```
127.0.0.1 traefik.domain.local web.domain.local stream_app.domain.local
```
