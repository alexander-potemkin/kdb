# Docker (on Ubuntu)

ToDo:
- Try https://github.com/jesseduffield/lazydocker


Run anything in one line

```
docker run -d --restart=unless-stopped --name='tinyproxy' -p 6666:8888 dannydirect/tinyproxy:latest ANY
```

**Installation one liner**

```bash
wget -O - https://raw.githubusercontent.com/Potemkin-Co/quicky/main/docker_ubuntu.sh | bash
```

## Optional: docker-compose

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker-compose --version
```

### Various docker commands

### make container always running (restart)

as per [StackOverflow](https://stackoverflow.com/questions/26852321/docker-add-a-restart-policy-to-a-container-that-was-already-created)

```bash
docker update --restart=always container_name
```

### Docker

```bash
sudo docker ps
sudo docker exec -it <container name> /bin/sh
```

Connect to the Docker instance

One-liner:

```bash
sudo docker exec -it `sudo docker ps --filter name=certbot -q` /bin/sh
```

Two liner:

```bash
sudo docker ps --filter name=srv-captain--mis -q
sudo docker exec -it $ID /bin/sh
```

Clear Docker build cache

```bash
sudo docker builder prune --all
```

Get resources map for the Dockers

```bash
sudo docker stats --all
```

```bash
sudo docker logs --follow 
```