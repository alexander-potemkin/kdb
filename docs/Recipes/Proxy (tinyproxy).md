# Proxy (tinyproxy)

<aside>
💡 **Deprecated**

</aside>

```bash
docker pull dannydirect/tinyproxy
docker run -d --restart=unless-stopped --name='tinyproxy' -p 6666:8888 dannydirect/tinyproxy:latest ANY
```

Then connect to the port 6666.

install Docker

```bash
wget -O - https://raw.githubusercontent.com/Potemkin-Co/quicky/main/docker_ubuntu.sh | bash
```

Start proxy server with password (from [Dockerhub](https://hub.docker.com/r/monokal/tinyproxy)):

```bash
docker run -d --restart=unless-stopped --name='tinyproxy' -p 65382:8888 --env BASIC_AUTH_USER=proxy_user --env BASIC_AUTH_PASSWORD=WZPq3K8dDY8y1Mh6xj5zIQ6vyxMK5JVFeXuJ monokal/tinyproxy:latest ANY
```

Start proxy server with IP restriction:

```bash
docker run -d --restart=unless-stopped --name='tinyproxy' -p 65382:8888 monokal/tinyproxy:latest $IP
```

# Useful commands

```bash
docker logs -f tinyproxy #for logs
```

Stat: [http://tinyproxy.stats/](http://tinyproxy.stats/)