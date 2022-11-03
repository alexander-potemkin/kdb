# Nessus server

- download dpkg from [https://www.tenable.com/downloads/nessus?loginAttempted=true](https://www.tenable.com/downloads/nessus?loginAttempted=true)
- upload deb to the destination server
- `sudo  dpkg -i *.deb` on the server
- `sudo service nessusd start`
- get license at [https://www.tenable.com/products/nessus/nessus-essentials](https://www.tenable.com/products/nessus/nessus-essentials) (with Chrome based engine)
- login at https://IP_address:8834 with Chrome based browser (not FireFox)
- done