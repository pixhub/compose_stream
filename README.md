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

Now make sure you got the git package, go into your home directory and download the repo :
```
cd /home/$USER
git clone https://github.com/pixhub/compose_stream
```

Go into the docker-compose.yml directory and lauch it
```
cd compose_stream/stream/
docker-compose up -d
```

Now, you can acces to Traefik Dashboard and Streaming Web page by typing the following in your Web Browser

Traefik Dashboard:
```
http://traefik.domain.local
```

Streaming Web Page :
```
https://web.domain.local
```

To stream into the server and watch it, get FFMPEG and type the following (Linux Only) :

Change the screen's resolution and adapt it to your srean size (here : 1920x1080)
```
ffmpeg -f x11grab -s 1920x1080 -framerate 30 -i $DISPLAY -f pulse -ac 2 -i default -c:v libx264 -preset fast -pix_fmt yuv420p -s 1920x1080 -c:a aac -b:a 160k -ar 44100 -threads 0 -f flv "rtmp://stream_app.domain.local:1935/live
```

Ok, now reload the http://web.domain.local web page clique on Play, and Enjoy !

Best regards,
pixhub.
