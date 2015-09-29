## Deploy container

### Login and change directory to your working directory
```
$ ssh -A egbert@dkr01.adcombi.com
$ cd Workspace/swagger-ui
```

### Pull and build
```
$ git pull origin master
$ docker build -t egbertp/swagger-ui:v1.0 .
```

### Check free ports using
```
$ docker ps
```

Run the docker container where you replace the x's for an number between 1 and 9 on a free port from the last step...
```
$ docker run -d -p 127.0.0.1:x000x:5000 egbertp/swagger-ui:v1.0
```

If you need to pass an environment variable, you can do that with the `-e` flag.
```
$ docker run -d -p 127.0.0.1:3000x:5000 -e TZ=Europe/Amsterdam egbertp/swagger-ui:v1.0

```
Note: see the 1Password tool for the full DATABASE_URL

### Configure NGINX reverse proxy

sudo nano `/etc/nginx/sites-enabled/swagger-ui.adcombi.com.vhost` and change the port to the corresponding port (e.g. 300002)

```
upstream swagger-ui {
    server 127.0.0.1:50002 max_fails=1 fail_timeout=10s;
}
```

Reload Nginx configuration

```
$ sudo service nginx reload
```

## Check logs

You can check the logs by referring to the docker container ID found with docker ps

```
$ docker logs -f 55c41add40d3
$ docker logs --tail=200 55c41add40d3
```

## Kil and destroy container

You can kill apps the same way, by referring to the docker container ID found with docker ps

* `rm` = remove
* `-f` = force (even when spinning)
* `-v` = also remove volumes

```
$ docker rm -f -v a30cc49985e7
```
