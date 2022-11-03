# Networking on Ubuntu

The content below is only for Ubuntu 18.04 and higher (the network has been changed dramatically in 18.04).

UFW on top of Docker (as per [the doc](https://github.com/chaifeng/ufw-docker))
``` bash
sudo wget -O /usr/local/bin/ufw-docker \
  https://github.com/chaifeng/ufw-docker/raw/master/ufw-docker
sudo chmod +x /usr/local/bin/ufw-docker
sudo ufw-docker install
sudo ufw-docker check
```

**Firewall check**

```bash
sudo ufw status verbose
sudo iptables -S
sudo iptables -nvL
```

B**asic firewall rules** ([ref](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-18-04#step-2-%E2%80%94-setting-up-default-policies))

```bash
sudo ufw allow ssh
sudo ufw allow proto tcp from any to any port 80,443 #HTTP & HTTPS
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw show added #shows rules, without enabling firewall
sudo ufw status numbered #shows rules, numbered
sudo ufw delete 2 #remove the rule
sudo ufw enable
sudo ufw disable
```

Enabling NAT (as per [article](https://askubuntu.com/questions/1050816/ubuntu-18-04-as-a-router))

```bash
sudo ufw show added #check status
sudo ufw enable
sudo ufw logging on

#optional
iptables --flush            # Flush all the rules in filter and nat tables    
iptables --table nat --flush    
iptables --delete-chain    # Delete all chains that are not in default filter and nat table    
iptables --table nat --delete-chain

sudo vi /etc/default/ufw #change to DEFAULT_FORWARD_POLICY="ACCEPT"
sudo vi /etc/ufw/sysctl.conf #uncomment net/ipv4/ip_forward=1 & net/ipv4/conf/all/forwarding=1

sudo vi /etc/ufw/before.rules #add the following at the very top
```

```bash
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]
# Forward traffic from eth1 (ens4) through eth0 (ens3).
-A POSTROUTING -s 192.168.168.0/24 -o ens3 -j MASQUERADE
#-A -> Append, -s -> source specification, -o -> out interface, -j -> where to jump
# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT
```

```bash
sudo ufw disable && sudo ufw enable
```

**Limiting an access for a specific network interface** ([ref](https://serverfault.com/questions/270715/ubuntu-ufw-set-a-rule-on-a-per-interface-basis))

> By default, ufw will apply rules to all available interfaces. To
limit  this,  specify DIRECTION on INTERFACE, where DIRECTION is
one of in or out (interface aliases  are  not  supported).   For
example,  to  allow  all  new incoming http connections on eth0,
use:

ufw allow in on eth0 to any port 80 proto tcp
> 

```bash
ufw allow in on eth1 to [eth1 ip addr] port 80 proto tcp
```

So, denying everything on public port and only enabling specific things would looks like the following:

```bash
sudo ufw default deny incoming on ens3 #default to public deny
sudo ufw allow in on ens4 from any to any #allow everything on LAN
sudo ufw allow out on ens4 from any to any #allow everything on LAN
sudo ufw enable #do disk snapshot first!

sudo ufw allow proto tcp on ens3 from any to any port 22
sudo ufw allow proto tcp from 10.66.66.0/24 to any port 80,443 #allow traffic via LAN

sudo ufw allow from 192.168.168.0/24 #allow from internal network
 
```

**Basic security features**

Move SSHd to another port

```bash
sudo vi /etc/sshd/sshd_config #change Port's 22 to anything you like
sudo service sshd restart #it shall be available on a new port

```

### Troubleshooting connections (good [doc here](https://help.mulesoft.com/s/article/How-to-capture-network-traffic-between-two-systems))

```bash
sudo tcpdump -vvv -n host IP
sudo tcpdump -vvv -i ens3 host IP port 22
sudo tcpdump -n -vvv -i ens3 'host IP and port 22'

```

### Configuring second network interface

<aside>
❗ DO NOT SPECIFY gateway4 - it's a [default gateway for all traffic](https://askubuntu.com/questions/1062902/ubuntu-18-04-netplan-static-routes), on all interfaces - unless you really know what to do.
It overrides the DHCP settings and you will lose access to your server.

</aside>

<aside>
❗ DO NOT USE TABS in YML files. Not on Ubuntu 18.04 at least. That break netplan ⇒ loosing network access to the server.

</aside>

<aside>
💡 It's safe to make configuration change in a separate file, then try out things with `sudo netplan --debug try --config-file ~/50-cloud-init.yaml`

</aside>

**Ubuntu 18.04 ([ref](https://serverspace.io/support/help/how-to-configure-static-ip-address-on-ubuntu-18-04/))**

```bash
cd /etc/netplan && ls
sudo vi 50-cloud-init.yaml

#file name starts with 50 something; it won't be overridden, as it's generated during the first init
```

Here is the resulting example file:

```bash
network:
    ethernets:
        ens3:
            addresses: []
            dhcp4: true
            optional: true
        **ens4:
               addresses: [192.168.168.10/24, ]**

    version: 2
```

```bash
sudo netplan --debug apply
```

**Ubuntu 20.04 ([ref](https://ostechnix.com/how-to-configure-ip-address-in-ubuntu-18-04-lts/))**

```bash
cd /etc/netplan && ls
sudo vi 01-netcfg.yaml
sudo netplan try
sudo netplan --debug apply
```

Here is the resulting example file:

```bash
network:
  ethernets:
    ens4:
      dhcp4: no
      addresses: 
        - 192.168.168.1/24

  version: 2
```

**Setting up routing for the second interface** (18.04; [ref](https://askubuntu.com/questions/1062902/ubuntu-18-04-netplan-static-routes/1062931#1062931?newreg=e938644cf7284879aa6c41b97ddad51c))

***Temporary* one:**

```bash
sudo route add -net 10.0.0.0/8 gw 192.168.1.1 eth0
sudo route del -host IP gw 192.168.168.1 ens4
sudo route add -host IP gw 192.168.168.10 ens4
sudo route add default gw 192.168.168.1 ens4
```

**Permanent one:**

```bash
sudo vi /etc/netplan/50-cloud-init.yaml
```

And add routes directive:

```bash
ens4:
               addresses: [192.168.168.10/24, ]
               routes:
                       - to: 10.0.0.0/8
                         via: 192.168.168.1
```

Check kernel level packets forward:

```bash
cat /proc/sys/net/ipv4/ip_forward
```

### Single interface configuration netplan:

```bash
network:
    ethernets:
        ens3:
               addresses: [192.168.168.22/24, ]
               gateway4: 192.168.168.1 
               routes:
                       - to: 10.0.0.0/8
                         via: 192.168.168.1
    version: 2
```

### One liners

Extract external IP address and add `1` at the end - which is usually a gateway.

```bash
ip addr show ens3 | awk '/inet/ {print $2}' | cut -d/ -f1 | head -1 | awk -F '.' '{ print $1"."$2"."$3"."1;}
```

or use 

```bash
sudo apt-get install sipcalc
sipcalc -I ens3
```

that gives first server in the network (which is usually a gateway)

```bash
sipcalc -I ens3 -i | grep "Usable range" | cut -d "-" -f 2 | xargs
```

Temporary setup default router

```bash

sudo route add default gw `sipcalc -I ens3 -i | grep "Usable range" | cut -d "-" -f 2 | xargs` ens3

```

Revoke routing back

```bash
sudo route del default gw `sipcalc -I ens3 -i | grep "Usable range" | cut -d "-" -f 2 | xargs` ens3
```