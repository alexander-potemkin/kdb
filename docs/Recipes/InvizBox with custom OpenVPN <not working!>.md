as per the [article](https://support.invizbox.com/hc/en-us/articles/115001828205):
- Open Admin interface (mobile app / [http://inviz.box](http://inviz.box/) - if not, check [this](https://support.invizbox.com/hc/en-us/articles/115000383069))
- Go to the Profiles page
- Select your Profile and enter Edit mode
- Enable SSH & Save settings
- Check if there are new firmware updates (better works from computer)
- Also make sure you associate that Profile with the intended Network(s) if not already done

as per the [article](https://www.invizbox.com/use-own-vpn-location-invizbox-go/):
- root@inviz.box # this will take a while, guess for DNS resolutions; password is the same as for WiFI
- at `etc/resolv.conf` replace nameserver with `1.1.1.1`
- `vi /etc/openvpn/myopenvpn.ovpn` and place a working OpenVPN config in there
- `vi /etc/config/vpn` back it up first; add the following lines
```
config active 'active'
	option server 'mygate'
	option country 'Whatever'
	option city 'WhatEver'
	option name 'mygate'
	option filename '/etc/openvpn/configs/myopenvpn.ovpn'
```
- `uci show vpn | less` to check if the config could be parsed
- reboot (I used `halt`, not sure it's a proper one).

### Doesn't work

- `/etc/resolv.conf` is overriden after the reboot
- OpenVPN connection can't be established
- interface fails to render any vpn option

I have also found wireguard config, which is kind of like shouldn't be there, as Wireguard is not suppored.
I guess those boxes doesn't really work well with 3rd party VPN.