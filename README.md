# quakejs-docker

### A fully local and Dockerized quakejs server. Independent, unadulterated, and free from the middleman.

The goal of this project was to create a fully independent quakejs server in Docker that does not require content to be served from the internet.
Hence, once pulled, this does not need to connect to any external provider, ie. content.quakejs.com. Nor does this server need to be proxied/served/relayed from quakejs.com

```
docker pull deyjcode/quakejs:latest
```
#### and run it:

```
docker run -d --name quakejs -e SERVER=<SERVER_NAME_OR_IP> -e HTTP_PORT=<HTTP_PORT> -p <HTTP_PORT>:80 -p 27960:27960 treyyoder/quakejs:latest
```

#### Example:

```
docker run -d --name deyjcodequakejs -e SERVER=stevequakejs.ddns.net -e HTTP_PORT=8080 -p 8080:80 -p 27960:27960 deyjcode/quakejs:1.0
```

#### Push
docker push deyjcode/quakejs:tagnumber

#### server.cfg:
Refer to [quake3world](https://www.quake3world.com/q3guide/servers.html) for instructions on its usage.

#### docker-compose.yml
```
version: '2'
services:
    quakejs:
        container_name: quakejs
        environment:
            - SERVER=10.0.0.2
            - HTTP_PORT=8080
        ports:
            - '8080:80'
            - '27960:27960'
        image: 'deyjcode/quakejs:latest'
```

Forked from https://github.com/treyyoder/quakejs-docker
