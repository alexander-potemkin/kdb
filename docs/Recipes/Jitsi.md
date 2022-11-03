# Jitsi

Jitsi's config files are at `/etc/prosody` (as per [this page](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-manual)).

Prepare clean empty server, that will only do the Jitsi conference for the people.

This guide follows scripted installation as per [this page](https://github.com/jitsi-contrib/installers/tree/main/jitsi-base).

Create A DNS records for  this server.


<aside>
💡 If server's memory is less than 8Gb, you might want to comment out 126 line of the script, that do 'exit' after that check.

</aside>

```bash
lsb_release -a # verify it's Ubuntu 20.04
sudo apt install wget
sudo apt-get update
sudo su -l
export JITSI_HOST=domain.com
export TURN_HOST=domain.com
wget -T 10 -O jitsi-base-installer https://raw.githubusercontent.com/jitsi-contrib/installers/main/jitsi-base/jitsi-base-installer
vi jitsi-base-installer # go to line 126 and disable exit
bash jitsi-base-installer
```

---


# Drafts; not working

# coTURN server install

Prepare DNS name and fixed IP address.

On Ubuntu 18.04 SSH to the server and go (as per [article](https://rajbharathmail.medium.com/create-stun-turn-server-in-ubuntu-18-04-aws-a59ef49c7659)):

```bash
sudo apt-get -y  update &&\
sudo apt-get -y install software-properties-common &&\
sudo add-apt-repository -y universe &&\
sudo add-apt-repository -y ppa:certbot/certbot &&\
sudo apt-get -y update &&\

sudo apt-get -y install coturn certbot

sudo certbot certonly --standalone #prepare DNS name & e-mail address

sudo vi /etc/default/coturn #TURNSERVER_ENABLED => 1
```

On Ubuntu 20.04:

```bash
sudo apt-get -y  update &&\
sudo apt-get -y install software-properties-common &&\
sudo add-apt-repository -y universe

sudo apt-add-repository -r ppa:certbot/certbot #confirm with ENTER
sudo apt-get -y update
sudo apt-get -y install coturn certbot

sudo certbot certonly --standalone #put **both** DNS names & e-mail address

sudo vi /etc/default/coturn #TURNSERVER_ENABLED => 1
```

`sudo cp /etc/turnserver.conf /etc/turnserver.conf.backup && sudo vi /etc/turnserver.conf`: 

```bash
server-name=coturn.uturn.domain.com
cert=/etc/letsencrypt/live/uturn.domain.com/cert.pem
pkey=/etc/letsencrypt/live/uturn.domain.com/privkey.pem
realm=uturn.domain.com
fingerprint
listening-ip=0.0.0.0
external-ip=IP
listening-port=443
min-port=10000
max-port=20000
log-file=/var/log/turnserver.log
verbose
#user=<YOUR_USERNAME>:<YOUR_PASSWORD>
lt-cred-mech
```

followed by:

```bash
sudo service coturn restart && sudo service --status-all | grep coturn
```

Then test (as per [the page](https://ourcodeworld.com/articles/read/1526/how-to-test-online-whether-a-stun-turn-server-is-working-properly-or-not)) by going to [https://webrtc.github.io/samples/src/content/peerconnection/trickle-ice](https://webrtc.github.io/samples/src/content/peerconnection/trickle-ice/), adding `sturn:uturn.domain.com:443`(protocol:domain:port) as a DNS name.

Then, click on "Gather candidates", wait until srflx candidate type to show up, which would confirm that a STUN server works fine.

# Jitsi server installation

Quick install without Docker, as per the [page](https://jitsi.github.io/handbook/docs/devops-guide/devops-guide-quickstart).

Setup Ubuntu 18.04 and a DNS name linked to the server static IP address.

Execute the following commands on it:

```bash
sudo apt update
sudo apt install apt-transport-https
sudo apt-add-repository universe
sudo apt update
sudo hostnamectl set-hostname meet.example.org
sudo bash
echo $(output=($(host $(hostname)));echo ${output[3]}) $(hostname) >> /etc/hosts && exit

```

When under CapRover - config is at `/config` (inside the Docker).

By default, Mute is after 10 people - turned to `false`

Troubleshooting guide: [https://community.jitsi.org/t/troubleshooting-steps-jitsi-meet-also-jibri-my-comprehensive-tips-for-the-beginner/38751](https://community.jitsi.org/t/troubleshooting-steps-jitsi-meet-also-jibri-my-comprehensive-tips-for-the-beginner/38751)