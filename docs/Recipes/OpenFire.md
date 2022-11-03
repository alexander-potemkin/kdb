To enable SSL certificates under Cloudron:

- nginx is running on the host (without Docker) and SSL certs are stored at `/home/yellowtent/platformdata/nginx/cert/`
  `openssl x509 -in certificate.pem -text`  to verify a certificate
- you can't mount that folder to Docker image, as only `/mnt`, `/media`, `/opt` and `/srv` could be mounted from within Cloudron
- `cd /srv && ln -s /home/yellowtent/platformdata/nginx/cert/`  and adding a _read-only_ mount creates `/media/NginxSSLCertificates/` folder inside OpenFire
- `/app/data/conf/security/hotdeploy` seems to be used for the certificates monitor extension

```bash
openssl pkcs12 -export -passout pass:changeit -in /etc/letsencrypt/live/<your-hostname>/fullchain.pem -inkey /etc/letsencrypt/live/<your-hostname>/privkey.pem -name <your-hostname> -out cert.p12

keytool -delete -keystore /opt/openfire/resources/security/keystore -alias <your-hostname> -storepass changeit -noprompt

keytool -importkeystore -deststorepass changeit -srcstorepass changeit -destkeystore /opt/openfire/resources/security/keystore -srckeystore cert.p12 -srcstoretype PKCS12 -deststoretype pkcs12

systemctl stop openfire
systemctl start openfire
```

or this [gist](https://gist.github.com/fabiomontefuscolo/317aeed542bc4bcd3959250f360c83f0) 

my problem now - it's to understand where are let's encrypt files... or shall I... I just need pkcs12 file

Here is what certbot generates, as per the documentation:

```
This directory contains your keys and certificates.

`privkey.pem`  : the private key for your certificate.
`fullchain.pem`: the certificate file used in most server software.
`chain.pem`    : used for OCSP stapling in Nginx >=1.3.7.
`cert.pem`     : will break many server configurations, and should not be used without reading further documentation (see link below).
```

Here is what I'm getting at Cloudron:
```
root@server:/home/yellowtent/platformdata/nginx/cert# file _.mydomain.co*
_.mydomain.co.cert: PEM certificate
_.mydomain.co.csr:  data
_.mydomain.co.key:  ASCII text
```

I guess I'm missing privkey.pem...  => it seems like I'm not, it's a `*.key` file, so:

`privkey.pem` => `_.mydomain.co.key`
`fullchain.pem`  => `_.mydomain.co.cert`

```
cd /app/data
openssl pkcs12 -export -passout pass:superpass -in /media/NginxSSLCertificates/_.mydomain.co.cert -inkey /media/NginxSSLCertificates/_.mydomain.co.key -name '*.mydomain.co' -out cert.p12

cp /app/resources/security/keystore keystore.backup
rm /app/resources/security/keystore

keytool -importkeystore -deststorepass superpass -srcstorepass superpass -destkeystore /app/resources/security/keystore -srckeystore cert.p12 -srcstoretype PKCS12 -deststoretype pkcs12

```

keytool command crashed the whole process, so I decided to go without Docker based setup and just use deb file (http://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_4.7.3_all.deb)

# Installing OpenFire on Ubuntu 20.04
```bash
export DOMAIN_NAME=<DOMAIN_NAME>
sudo apt update && sudo apt upgrade
sudo apt install default-jdk certbot python3-certbot-nginx nginx
wget http://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_4.7.3_all.deb
sudo dpkg -i *openfire*.deb # ignore the /var/lib/openfire warning
sudo service openfire status
```

Install 'Certificate Manager' plugin, this will create `hotdeploy` directory, return back to the command line

```bash
sudo tee -a /etc/letsencrypt/renewal-hooks/post/openfire.sh  > /dev/null <<EOT
#!/bin/bash
cp /etc/letsencrypt/live/$DOMAIN_NAME/privkey.pem /usr/share/openfire/resources/security/hotdeploy/$DOMAIN_NAME-privkey.pem
cp /etc/letsencrypt/live/$DOMAIN_NAME/fullchain.pem /usr/share/openfire/resources/security/hotdeploy/$DOMAIN_NAME-fullchain.pem
chown openfire:openfire /usr/share/openfire/resources/security/hotdeploy/*
EOT

sudo chmod +x /etc/letsencrypt/renewal-hooks/post/openfire.sh

sudo certbot certonly --standalone --agree-tos -d $DOMAIN_NAME --register-unsafely-without-email # optional --email <YOUR_EMAIL> 

sudo certbot --nginx --agree-tos -d '*.'$DOMAIN_NAME --register-unsafely-without-email


```

Dashboard will still show error message, which seems to be fixed by (as per [forum thread](https://discourse.igniterealtime.org/t/a-certificate-for-the-domain-of-this-server-is-missing-error-despite-the-certificate-is-there/92177) by a wildcard certificate or specific mentions of the certificates required.

Wildcard let's encrypt certificate is an issue, as it require DNS challenge, that can't be automated in most of the DNS providers. But here is a [gist](https://gist.github.com/utek/ba08e9ed8208342817743c0cc25ab697) on how to call DNS challenge, if an option would be found.

Waiting for the feedback on the [forum thread](https://discourse.igniterealtime.org/t/a-certificate-for-the-domain-of-this-server-is-missing-error-despite-the-certificate-is-there/92177)  on this since 2022-10-26

Pick up on the terminal by: `export $DOMAIN_NAME=xmpp.mydomain.co`

**ToDo:**
- cron certbot execution
- check STUN server plugin



**Drafts:**

```

sudo certbot certonly --standalone --agree-tos -d $DOMAIN_NAME --register-unsafely-without-email # optional --email <YOUR_EMAIL> 

sudo openssl pkcs12 -export -passout pass:mypass -in /etc/letsencrypt/live/$DOMAIN_NAME/fullchain.pem -inkey /etc/letsencrypt/live/$DOMAIN_NAME/privkey.pem -name $DOMAIN_NAME -out cert.p12

sudo cp /usr/share/openfire/resources/security/keystore keystore.backup

keytool -delete -keystore /usr/share/openfire/resources/security/keystore -alias $DOMAIN_NAME -storepass changeit -noprompt

sudo keytool -importkeystore -deststorepass changeit -srcstorepass mypass -destkeystore /usr/share/openfire/resources/security/keystore -srckeystore cert.p12 -srcstoretype PKCS12 -deststoretype pkcs12

chown openfire:openfire /usr/share/openfire/resources/security/keystore

systemctl restart openfire
sudo netstat -tulnp | grep java

```

open http://DOMAIN:9090/ to configure the server (HTTPS will be configured later on)

`sudo vi /etc/letsencrypt/renewal-hooks/post/openfire.sh`

Some findings:

> privkey is your private key. It is not the same as a Certificate Signing Request (CSR) file. Don't ever send the private key offsite. It's never meant to be seen by your CA (Letsencrypt or otherwise).

> However, you should be able to import the private key and the generated certificate file from Letsencrypt back into your Java based application such as openfire. I don't exactly know the keytool commands to run but it should be simple enough to read the man page/online searches.

> That's the traditional way of doing it. You create a CSR file which is an intermediate type of file.

> Then you open this file, copy its contents, go to your CA's website, login and paste it into some kind of web form. Then you hit submit and wait.

> CA does its thing in the background, verifies you own the domain, etc.

> Then eventually it'll tell you it's done and you can download the certificate and CA's own public certificate file.

> You then take those files, copy them to your server and configure the software to use them.

> When the certificate is up for renewal, you repeat the above process. It's all very manual.

> The link you provided is not meant to be used with an SSL provider such as Letsencrypt. It's meant to be used with the more traditional SSL providers.

> LE automates everything and is then supposed to automatically install the certificate in the software. OpenFire does not seem to support this so you have to do a manual letsencrypt process (IE using DNS as a method) or find scripts online written by people that have created the missing "glue" to automate it anyway.

> You're better off looking through OpenFire's forums for people that use Letsencrypt and have already automated it for you. That, or do Letsencrypt manually and every 2 or so months, repeat. That's even more laborious (but still free).