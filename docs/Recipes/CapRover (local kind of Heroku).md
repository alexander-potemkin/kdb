# CapRover (local kind of Heroku)

<aside>
❗ If the app is not adapted to Heroku or was not adapted to CapRover earlier, a *captain_definition* file has to be added, as it's the one that lets CapRover knows which stack it's launching, examples [available](https://github.com/caprover/caprover/tree/master/captain-sample-apps).

</aside>

### Prerequisite

- server (Ubuntu 18.04 LTS) and ssh access
- DNS A type record (to the server's IP)
- e-mail address for HTTPS registration (could be a fake one)
- network ports opened as per [CapRover documentation](https://caprover.com/docs/firewall.html):

```bash
ufw allow 80,443,3000,996,7946,4789,2377/tcp; ufw allow 7946,4789,2377/udp;
```

Only 80 & 443 ports need to be opened to the public internet (as per [ticket](https://github.com/caprover/caprover/issues/990)) + 22 for SSH.

Quick setup is available here: [https://github.com/caprover/caprover-cli#server-setup](https://github.com/caprover/caprover-cli#server-setup)

### Installing CapRover

Configure server’s timezone to ease troubleshooting later:

```bash
sudo dpkg-reconfigure tzdata #change timezone
```

Install Docker first:

```bash
wget -O - https://raw.githubusercontent.com/alexander-potemkin/quickies/main/docker_ubuntu.sh | bash
```

Then actual version of npm & node.js

```bash
wget -O - https://raw.githubusercontent.com/alexander-potemkin/quickies/main/nodejs16.sh | bash
```

Then an actual CapRover

```bash
wget -O - https://raw.githubusercontent.com/alexander-potemkin/quickies/main/caprover_setup.sh | bash
```

followed by

```bash
curl ifconfig.io #to get an IP address of the server
```

and the content of JSON as follows (as per [doc](https://github.com/caprover/caprover-cli/blob/master/readme.md)):

```bash
{
  "caproverIP": "127.0.0.1",
  "caproverPassword": "captain42",
  "caproverRootDomain": "domain_name",
  "newPassword": "",
  "certificateEmail": "your@email.com",
  "caproverName": "captain-01"
}
```

Applied by:

```bash
caprover setup -c caprover.json
```

There is also interactive setup - `caprover serversetup` :

Now go to [http://IP_address:3000](http://ip_address:3000) (note HTTP, without `**S`**) port, and proceed with `captain42` as a default password.

### DNS configuration

create DNS record like that one:

*.sub-domain A 1H IP address

1. At the Dashboard, link with DNS name: `lhk.domain.name` 
2. After CapRover updates to HTTPS, at Chrome type `thisisunsafe` to ignore invalid SSL certificate.
3. Enable HTTPS
4. Enjoy!

### Logs monitoring

Install Dozzle from one click apps, as per this advice: https://github.com/caprover/caprover/issues/1140

### GitHub Deployment keys

 `ssh-keygen -m PEM -t rsa -b 4096 -C projectname` , enter `./id_rsa` and get the keys.

`cat id_rsa` and send that to CapRover's Deployment page

 `cat id_rsa.pub` and deliver that key to GitHub's Deployment Key (under settings of repository) 

### Automatic updates with the source code

Gather webhook URL from CapRover settings.

GitHub → Repository → Settings → Webhooks →add it there,  

### SSL certificate update

```bash
sudo docker exec `sudo docker ps --filter name=certbot -q` /usr/local/bin/certbot renew #-it for interactive
```

### One-click app update

[https://github.com/caprover/caprover/issues/1008](https://github.com/caprover/caprover/issues/1008)

### Various
SSL certificates are stored at the host Linux at ` /home/yellowtent/platformdata/nginx/cert/`

### Troubleshooting CapRover

**Cleaning up cache** 

**Don't do that, unless absolutely required. Can have unexpected side effects.**

as per [GitHub issue](https://github.com/caprover/caprover/issues/1135)

```bash
docker builder prune --all
```

[https://caprover.com/docs/troubleshooting.html](https://caprover.com/docs/troubleshooting.html)

CapRover logs

```bash
docker service logs captain-captain --since 60m --follow
```

From the server

```bash
sudo docker exec -it `sudo docker ps --filter name=srv-captain -q` /bin/sh
```

Password reset

```bash
sudo su -
apt install jq
docker service scale captain-captain=0
cp /captain/data/config-captain.json /captain/data/config-captain.json.backup
jq 'del(.hashedPassword)' /captain/data/config-captain.json > /captain/data/config-captain.json.new
cat /captain/data/config-captain.json.new > /captain/data/config-captain.json
rm /captain/data/config-captain.json.new
# set a temporary password
docker service update --env-add DEFAULT_PASSWORD=captain42 captain-captain
docker service scale captain-captain=1
```

### Restart CapRover

```bash
docker service update captain-captain --force
```

### Removing CapRover

```bash
docker service rm $(docker service ls -q)
## remove CapRover settings directory
rm -rf /captain
## leave swarm if you don't want it
docker swarm leave --force
## full cleanup of docker
docker system prune --all --force
```