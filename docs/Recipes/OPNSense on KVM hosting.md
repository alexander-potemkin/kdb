Download from https://opnsense.org/download/

Didn't try dvd & vga images.
Serial as a CD-ROM didn't boot - could not read from cdrom (code 0005).

For nano image login with “root” and password “opnsense”.
Choose option 1 to assign interfaces (WAN/LAN)
Choose option 2 and configure IP address.

If you need to access admin GUI from the outside (WAN) then disable the firewall first by `pfctl -d`, create a firewall rule to access 443 port via WAN, then do `pfctl -e` (as per https://docs.freebsd.org/en/books/handbook/firewalls/)

Go to the web interface.

When doing port forward (NAT), keep in mind, that it won't work, if the destination server won't look back to the firewall (destination unreacheable and non routeable).

API call for Firewall:
`curl -k -u "":"" "https://IP:62309/api/firewall/filter/searchRule/"`; API token to be done inside the user profile page