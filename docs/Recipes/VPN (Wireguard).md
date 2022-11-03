# VPN (Wireguard)

## Server

Routing thing: [https://www.poftut.com/add-new-route-ubuntu-linux/](https://www.poftut.com/add-new-route-ubuntu-linux/)

sudo route add -net 10.0.0.0/8 gw 192.168.168.1 ens4

<aside>
❗ Use Ubuntu 20.04 LTS (18.04 has a mess with wireguard availability).

</aside>

### Wireguard configuration (as per [that script](https://github.com/angristan/wireguard-install))

```bash
curl -O https://raw.githubusercontent.com/angristan/wireguard-install/master/wireguard-install.sh
chmod +x wireguard-install.sh
sudo ./wireguard-install.sh
```

<aside>
❗ Make sure to add `PersistentKeepalive = 25`  in the 'Peer' section, at the end of each key file manually.
Or, alter the script, near 290-s lines:

`[Peer]
PublicKey = ${SERVER_PUB_KEY}
PresharedKey = ${CLIENT_PRE_SHARED_KEY}
Endpoint = ${ENDPOINT}
AllowedIPs = 0.0.0.0/0,::/0
PersistentKeepalive = 25" >>"${HOME_DIR}/${SERVER_WG_NIC}-client-${CLIENT_NAME}.conf"`

</aside>

As a nice addition to the keys adding process, the following line near 313 line of the script save some time: `cat "${HOME_DIR}/${SERVER_WG_NIC}-client-${CLIENT_NAME}.conf"`

For the office computers with internal network AND to the intranet (192.168.168.0/24), add that:

```bash
AllowedIPs = 1.0.0.0/8, 2.0.0.0/8, 3.0.0.0/8, 4.0.0.0/6, 8.0.0.0/7, 11.0.0.0/8, 12.0.0.0/6, 16.0.0.0/4, 32.0.0.0/3, 64.0.0.0/2, 128.0.0.0/3, 160.0.0.0/5, 168.0.0.0/6, 172.0.0.0/12, 172.32.0.0/11, 172.64.0.0/10, 172.128.0.0/9, 173.0.0.0/8, 174.0.0.0/7, 176.0.0.0/4, 192.0.0.0/9, 192.128.0.0/11, 192.160.0.0/13, 192.168.168.0/24, 192.169.0.0/16, 192.170.0.0/15, 192.172.0.0/14, 192.176.0.0/12, 192.192.0.0/10, 193.0.0.0/8, 194.0.0.0/7, 196.0.0.0/6, 200.0.0.0/5, 208.0.0.0/4, 94.140.14.14/32, 94.140.15.15/32
```

All traffic's AllowedIPs is `0.0.0.0/0, ::/0`.

Just the cloud traffic AllowedIPs is  `192.168.168.0/24, IP/32, IP/32` - which is intranet network and DNS server's IPs with /32 network on it.

Working note: netmask 255.255.255.0 network is in use.

Server side (very limited) logging:

```bash
sudo su -
echo "module wireguard +p" | tee /sys/kernel/debug/dynamic_debug/control
touch /var/log/wireguard.log
nohup dmesg -T --follow | egrep "(wireguard:|wg0)" >> /var/log/wireguard.log
```

Some usefull commands:

```bash
wg show all dump
```

Generate QR code

```bash
qrencode -t ansiutf8 -l L < ...conf #to generate QR code
```

Various:

```bash
# sudo vi /etc/sysctl.conf
# sudo sysctl -p
net.ipv4.ip_forward = 1
```

### Adding WireGuard to NetworkManager GUI on Ubuntu 20.04 based

The result feels like sucks.

as per [the doc](https://github.com/max-moser/network-manager-wireguard/issues/50#issuecomment-922104777):

```bash
sudo apt install wireguard git dh-autoreconf libglib2.0-dev intltool build-essential libgtk-3-dev libnma-dev libsecret-1-dev network-manager-dev resolvconf
git clone https://github.com/max-moser/network-manager-wireguard
cd network-manager-wireguard
./autogen.sh --without-libnm-glib

./configure --without-libnm-glib --prefix=/usr --sysconfdir=/etc --libdir=/usr/lib/x86_64-linux-gnu --libexecdir=/usr/lib/NetworkManager --localstatedir=/var

make
sudo make install
```

Now go to the network manager GUI and create WireGuard connection from there.

### Configuring client

As per [the page](https://www.cyberciti.biz/faq/how-to-import-wireguard-profile-using-nmcli-on-linux/).

```bash
sudo apt install wireguard #if required
```

1. Importing WireGuard config into network manager:

```bash
nmcli connection import type wireguard file $file
```

1. Check the import is good:

```bash
nmcli connection show #network manager
sudo wg show #in Wireguard

#in more details
nmcli connection show $connection_name
sudo wg show $if_name 
```

1. Bring connection up or down

```bash
nmcli connection up $connection_name
nmcli connection down $connection_name
```

```bash

nmcli connection add type wireguard ifname wg0 con-name my-wg0
nmcli connection import type wireguard file wg.conf
nmcli --show-secrets --ask connection up wg
nmcli --show-secrets --ask connection down wg

CONF_FILE="wg-ru.conf"
nmcli connection add type wireguard ifname wg1 con-name wg-ru
nmcli connection import type wireguard file $CONF_FILE
nmcli --show-secrets --ask connection up wg-ru
#nmcli connection modify type wireguard file wg.conf
```

ToDo:

- check for [https://www.procustodibus.com/](https://www.procustodibus.com/)

---

### Archive

---

sysctl net.ipv4.ip_forward=1

[https://github.com/angristan/wireguard-install/blob/master/wireguard-install.sh](https://github.com/angristan/wireguard-install/blob/master/wireguard-install.sh)

There is no such parameter in WireGuard as, clients can go quiet at any time and expect to be able to talk to the server again at any time later.

Specifically, the protocol requires a client to handshake with the server to begin a session. To maintain the session a client must handshake at least once every 180 seconds. In practice, the handshake happens some time between 120 and 180 seconds.

If a client stops talking and at a later time wants to start talking again, providing the server is active then,if the time since last talking is:

<120 seconds, carry on as normal

> =120 seconds, <=180 seconds carry on and handshake within 60 seconds.
180 seconds, handshake and carry on
The server and client maintain timers so that they always know what to do and when to do it.
> 

Thus, WireGuard is a connectionless protocol and there is no need to worry about timeouts. A client is either talking (and handshaking as required) or silent.

[https://serverfault.com/questions/1045653/set-vpn-connection-timeout-in-wireguard](https://serverfault.com/questions/1045653/set-vpn-connection-timeout-in-wireguard)

[https://github.com/pirate/wireguard-docs](https://github.com/pirate/wireguard-docs)

### FreeBSD stuff

rxtun option

[https://discuss.vultr.com/discussion/979/freebsd-vtnet0-tuning](https://discuss.vultr.com/discussion/979/freebsd-vtnet0-tuning)

[https://forums.openvpn.net/viewtopic.php?t=25039](https://forums.openvpn.net/viewtopic.php?t=25039)

`dd if=/dev/random of=myfile.dat bs=$(( 1024 * 1024 )) count=100`

### OpenVPN Linux stuff

[https://github.com/angristan/openvpn-install](https://github.com/angristan/openvpn-install) → seems to be more mature

[https://github.com/Nyr/openvpn-install](https://github.com/Nyr/openvpn-install)

[https://www.linux-kvm.org/page/Tuning_KVM](https://www.linux-kvm.org/page/Tuning_KVM)

### VyOS

Didn't really like it, feels like too much complicated, not mature / supported / stable enough to trust it completely. Would rather choose \*BSD based router

[https://blog.kroy.io/2019/08/23/battle-of-the-virtual-routers/#Final_Results](https://blog.kroy.io/2019/08/23/battle-of-the-virtual-routers/#Final_Results)

[https://www.reddit.com/r/networking/comments/2g9nh6/linux_routers_and_your_thoughts/](https://www.reddit.com/r/networking/comments/2g9nh6/linux_routers_and_your_thoughts/)

[https://vyos.io/subscriptions/support/](https://vyos.io/subscriptions/support/)