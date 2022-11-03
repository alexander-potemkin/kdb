# 1Password to Bitwarden migration

1. Export all of your data from 1Password
2. Use Bitwarden (even if self-hosted) to upload data - don't do scripts or anything else.
3. Sync to your clients. Profit.

Reference:

- [https://bitwarden.com/help/cli/#config](https://bitwarden.com/help/cli/#config)
- [https://bitwarden.com/help/cli/](https://bitwarden.com/help/cli/)
- [https://bitwarden.com/help/import-from-1password/](https://bitwarden.com/help/import-from-1password/)


# Yandex Cloud

Easy way to decrease cost for the server - for UAT, for example: setup interruptible server and the following cron task on another (for example - production) server:

```bash
#(re)start interruptible server
* * * * * /home/alexander/yandex-cloud/bin/yc compute instance start epddddid8tvfjnpm36fa
```

Requires yc command tool install.


# Telegram

To get chat id:

Invite @RawDataBot to your group.

Upon joining it will output a JSON file where your chat id will be located at [message.chat.id](http://message.chat.id/).


# Publii

Theme installation is happening via three dots menu at the Publii interface.

# Prettier

```
npm install prettier
npx prettier --write "./public/**/*.(json|yml)"
```


# SendGrid troubleshooting

1. To check if API key is valid:

```
GET https://api.sendgrid.com/v3/scopes
with header:
authorization => Bearer $TheAPIKey
```

To send mails, `mail.send` permission must be there:

```
{
	"scopes": [
		"mail.send",
		"sender_verification_eligible",
		"2fa_required"
	]
}
```


# Ubuntu - Remap your mouse button(s)

Used it to map third button for 'Expose' like.

sudo apt install git python3-setuptools gettext
git clone [https://github.com/sezanzeb/key-mapper.git](https://github.com/sezanzeb/key-mapper.git)
cd key-mapper && ./scripts/build.sh
sudo apt install ./dist/key-mapper-1.2.1.deb

keyboard → shortcuts → show the window selection screen → map some key (F7 in my case), then add desired button (middle mouse button in my case) to F7 - enjoy!

# Traffic forward using sockets (for VPN/Wireguard block, for example)

```bash
nohup socat UDP4-RECVFROM:65326,fork UDP4-SENDTO:$IP:65326
```

Related docs:

[https://mattryall.net/blog/udp-port-forwarding-with-socat](https://mattryall.net/blog/udp-port-forwarding-with-socat)

[https://www.redhat.com/sysadmin/getting-started-socat](https://www.redhat.com/sysadmin/getting-started-socat)

[https://serverfault.com/questions/457433/proxy-with-netcat-forever](https://serverfault.com/questions/457433/proxy-with-netcat-forever)

[https://trailofbits.github.io/algo/client-linux-wireguard.html](https://trailofbits.github.io/algo/client-linux-wireguard.html)

[https://upcloud.com/community/tutorials/get-started-wireguard-vpn/](https://upcloud.com/community/tutorials/get-started-wireguard-vpn/)


# ngrok

1. Register at [ngrok.com](http://ngrok.com) 
2. Download Go to [https://dashboard.ngrok.com/get-started/setup](https://dashboard.ngrok.com/get-started/setup)

```bash
sudo apt install snapd
snap install ngrok
ngrok authtoken 27ABEkIoyq1tFZtNpSc7CyDWuij_XedjVR8ekD8akuzeCrB4
ngrok http 80
ngrok help
```


# Node.js on Ubuntu 20.04

As per [the article](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-20-04):

```bash
curl -sL https://deb.nodesource.com/setup_16.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install -y nodejs
node -v
```