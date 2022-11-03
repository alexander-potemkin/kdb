# Server setup
```bash
# Generic part
sudo su -
apt update && apt upgrade
fallocate -l 1G /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
swapon --show
echo "/swapfile    none    swap    sw    0   0" >> /etc/fstab
apt install -y unattended-upgrades update-notifier-common apt-listchanges

vim /etc/apt/apt.conf.d/50unattended-upgrades
unattended-upgrades --dry-run

dpkg-reconfigure tzdata

# OpenVPN server preparation
curl -O https://raw.githubusercontent.com/angristan/openvpn-install/master/openvpn-install.sh
chmod +x openvpn-install.sh
sudo ./openvpn-install.sh # Ctrl + C it before creating new user
sudo sh -c 'echo "set_var EASYRSA_CERT_EXPIRE 3600" >> /etc/openvpn/easy-rsa/vars' # to extend certificates to almost 10 years
sudo sh -c 'echo "local 127.0.0.1" >> /etc/openvpn/server.conf'

sudo sh -c 'echo "route `curl -s ifconfig.co` 255.255.255.255 net_gateway" >> /etc/openvpn/client-template.txt'
sudo sed -e '/^remote / s/^#*/#/' -i /etc/openvpn/client-template.txt # possible issue check: grep remote-cert-tls /etc/openvpn/client-template.txt - it should be not commented
sudo sh -c 'echo "remote 127.0.0.1 1984" >> /etc/openvpn/client-template.txt'

# Cloak server installation
sudo su -
apt update && apt install -y nginx certbot python3-certbot-nginx net-tools

# have DNS name binded to the server
certbot --nginx --register-unsafely-without-email # choose redirect all HTTP traffic to HTTPS

sed -e 's/listen 443 ssl;/listen 6443 ssl;/' -i /etc/nginx/sites-available/default
sed -e 's/listen \[::\]:443 ssl ipv6only=on;/listen \[::\]:6443 ssl ipv6only=on;/' -i /etc/nginx/sites-available/default
systemctl restart nginx
netstat -tulnp | grep 443 | grep -v 6443 # shall be empty

wget https://github.com/cbeuw/Cloak/releases/download/v2.6.0/ck-server-linux-amd64-v2.6.0
chmod +x ck-server-linux-amd64-v2.6.0 && cp ck-server-linux-amd64-v2.6.0 /usr/local/bin/ck-server
setcap CAP_NET_BIND_SERVICE=+eip /usr/local/bin/ck-server

ck-server -key | tee cloak.keys
cat cloak.keys | tail -1 | awk --field-separator=":" '{print $2}' | xargs | cut -c 6- > cloak-private.key
cat cloak.keys | head -1 | awk --field-separator=":" '{print $2}' | xargs | cut -c 6- > cloak-public.key
ck-server -u | tee cloak-admin.key #admin
ck-server -u | tee cloak-user.key #first user
mkdir /etc/cloak

# adjust OpenVPN port (1194) here is you installed OpenVPN on a non-standard port
sudo tee -a /etc/cloak/ckserver.json  > /dev/null <<EOT
{
  "ProxyBook": {
    "openvpn": [
      "tcp",
      "127.0.0.1:1194"
    ]
  },
  "BindAddr": [
    ":443"
  ],
  "BypassUID": [
    "CLOAK-USER-KEY"
  ],
  "RedirAddr": "127.0.0.1:6443",
  "PrivateKey": "CLOAK-PRIVATE-KEY",
  "AdminUID": "CLOAK-ADMIN-KEY",
  "DatabasePath": "/etc/cloak/userinfo.db",
  "StreamTimeout": 300
}
EOT

sed "s/CLOAK-USER-KEY/`cat cloak-user.key`/" -i /etc/cloak/ckserver.json
sed "s/CLOAK-ADMIN-KEY/`cat cloak-admin.key`/" -i /etc/cloak/ckserver.json
sed "s|CLOAK-PRIVATE-KEY|`cat cloak-private.key`|" -i /etc/cloak/ckserver.json

sudo ck-server -c /etc/cloak/ckserver.json -verbosity Trace # if no errors, Ctrl + C and go forward

sudo tee -a ~/ckclient.json > /dev/null <<EOT
{
  "Transport": "direct",
  "ProxyMethod": "openvpn",
  "EncryptionMethod": "aes-gcm",
  "UID": "CLOAK-USER-KEY",
  "PublicKey": "CLOAK-PUBLIC-KEY",
  "ServerName": "CLOAK-DNS-NAME",
  "NumConn": 8,
  "BrowserSig": "chrome",
  "StreamTimeout": 300,
  "RemoteHost": "CLOAK-DNS-NAME",
  "RemotePort": "443"
}
EOT

sed "s/CLOAK-USER-KEY/`cat cloak-user.key`/" -i ~/ckclient.json
sed "s|CLOAK-PUBLIC-KEY|`cat cloak-public.key`|" -i ~/ckclient.json
sed "s/CLOAK-DNS-NAME/YOURDNSNAME/g" -i ~/ckclient.json # replace with your DNS name

#path as per man 5 systemd.unit
sudo tee -a /etc/systemd/system/cloak.service  > /dev/null <<EOT
[Unit]  
Description=Cloak Server  
After=network.target  
  
[Service]  
Type=simple  
ExecStart=/usr/local/bin/ck-server -c /etc/cloak/ckserver.json  
Restart=on-failure  
  
[Install]  
WantedBy=multi-user.target
EOT


systemctl enable cloak
systemctl start cloak
systemctl status cloak
ss -tulpn | grep 443

```

# Linux client
Install the client (for 22.04 LTS; for others modify URL as per [this](https://openvpn.net/cloud-docs/openvpn-3-client-for-linux/#:~:text=Type%20the%20following%20command%20into%20the%20Terminal:%20sudo%20apt%20update,install%20the%20OpenVPN%203%20package) page)
```
sudo apt install apt-transport-https
sudo wget https://swupdate.openvpn.net/repos/openvpn-repo-pkg-key.pub
sudo apt-key add openvpn-repo-pkg-key.pub
sudo wget -O /etc/apt/sources.list.d/openvpn3.list https://swupdate.openvpn.net/community/openvpn3/repos/openvpn3-jammy.list
sudo apt update
sudo apt install openvpn3
```

`start script`
```bash
#!/bin/bash
set -x
set -e

if [ ! -f "ck-client" ]; then
    wget https://github.com/cbeuw/Cloak/releases/download/v2.6.0/ck-client-linux-amd64-v2.6.0
	chmod +x ck-client-linux-amd64-v2.6.0 && mv ck-client-linux-amd64-v2.6.0 ck-client
fi

if [ ! -f "ckclient.json" ]; then
    echo "Cloak config file missing";
    exit 1;
fi

sudo rm -f /tmp/cloak.log /tmp/openvpn.log
echo "Starting Cloak"
sudo nohup ./ck-client -c ckclient.json  -verbosity Info &> /tmp/cloak.log &
sudo tail /tmp/cloak.log
echo "A little break"
sleep 5
sudo nohup openvpn3 session-start --config *.ovpn &> /tmp/openvpn.log &
```

`stop script`
```bash
#!/bin/bash
sudo openvpn3 sessions-list
sudo openvpn3 session-manage --config *.ovpn --disconnect
sudo killall ck-client
#while true; do clear && sudo openvpn3 log --log-level 6 --config *.ovpn; sleep 1; done

```

`status script`
```bash
#!/bin/bash
sudo openvpn3 sessions-list
sudo openvpn3 log --log-level 6 --config *.ovpn
```


# MacOS client
Download [stable version of TunnelBlick](https://tunnelblick.net/downloads.html) OpenVPN client.
`cloak.sh`
```bash
#!/bin/bash

if [ ! -f "ck-client" ]; then
	wget https://github.com/cbeuw/Cloak/releases/download/v2.6.0/ck-client-darwin-amd64-v2.6.0
	chmod +x ck-client-darwin-amd64-v2.6.0 && mv ck-client-linux-amd64-v2.6.0 ck-client
fi

if [ ! -f "ckclient.json" ]; then
    echo "Cloak config file missing";
    exit 1;
fi

./ck-client -c ckclient.json
```


# Windows client
Download [Community edition](https://openvpn.net/community-downloads/) of the OpenVPN client
```
curl.exe -L -o ck-client.exe https://github.com/cbeuw/Cloak/releases/download/v2.6.0/ck-client-windows-amd64-v2.6.0.exe
.\ck-client -c ckclient.json
```

`start.bat`
```
.\ck-client -c ckclient.json
```

# Adding new clients
- ssh to cloaked openvpn server
- create new openvpn client with the script
- pass over template connection folder + personal script to be installed by a HelpDesk

# Securing
- change nginx to `listen` on `127.0.0.1:6443` to ensure it's not available from the outside at all
- if you apply `ufw` than be aware that an access of the internal hosts might not be available

# Troubleshooting
- Cloak logging library is [logrus](https://github.com/sirupsen/logrus) , Trace, Debug, Info, Warning, Error, Fatal and Panic logging options available
- Client side logs are at `/tmp/cloak.log`  & `/tmp/openvpn.log`; server side logs are at syslog
- Server side cloak configs are at `sudo su -`
- add `management 127.0.0.1 5555` to `/etc/openvpn/server.conf`, followed by `sudo service openvpn restart` to enable `telnet 127.0.0.1 5555` which will respond to `status` command
 - Before anything, verify the ports are correct

Server HW note: 20Gb HDD, 2GB RAM, 2GHz CPU