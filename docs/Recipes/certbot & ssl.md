# certbot wildcard
- digital ocean plugin and config: https://www.digitalocean.com/community/tutorials/how-to-acquire-a-let-s-encrypt-certificate-using-dns-validation-with-certbot-dns-digitalocean-on-ubuntu-20-04
- gandi plugin: https://github.com/obynio/certbot-plugin-gandi
- and that seems to be a hexonet plugin: https://gist.github.com/gfdsa/f35272ec22277412068f96e6dc13cac3

### Gandi certbot plugin
```bash
sudo pip install certbot-plugin-gandi

sudo tee -a /etc/letsencrypt/gandi.ini > /dev/null <<EOT
# live dns v5 api key
dns_gandi_api_key=APIKEY

# optional organization id, remove it if not used
# dns_gandi_sharing_id=SHARINGID
EOT

sudo chmod 600 /etc/letsencrypt/gandi.ini

sudo certbot certonly --authenticator dns-gandi --dns-gandi-credentials /etc/letsencrypt/gandi.ini --server https://acme-v02.api.letsencrypt.org/directory -d $DOMAIN_NAME -d \*.$DOMAIN_NAME

```

ToDo:
- certificates copy script probably doesn't always work - add it to be checked later on
- cron `0 0 * * 0 certbot renew -q --authenticator dns-gandi --dns-gandi-credentials /etc/letsencrypt/gandi/gandi.ini --server https://acme-v02.api.letsencrypt.org/directory` as per [this doc](https://github.com/obynio/certbot-plugin-gandi)

# ssl

## Check SSL certificate info from the command line
`openssl s_client -connect hostname:443 -showcerts`

## nginx & certbot

Quite a nice DigitalOcean doc is [here](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-18-04).

```bash
sudo nginx -t #check configuration file
sudo systemctl reload nginx #nginx to reread configuration changes; if problems - see below
sudo certbot --nginx -d DNS_NAME_1 -d DNS_NAME_2 #certbot SSL certificate configuration
sudo certbot renew --dry-run #check how certificate renewal would work
systemctl list-timers #check if certbot will renew via system
crontab -l #check crontab
```

One more instruction: [https://certbot.eff.org/instructions?ws=nginx&os=ubuntu-18](https://certbot.eff.org/instructions?ws=nginx&os=ubuntu-18)

### certbot force renewal

```bash
certbot renew --force-renewal
```

### Troubleshoting

Let's Encrypt certbot do configuration files backup, before any chnages, that could be found at `/var/lib/letsencrypt/backups/`  (VERY handy when nginx stops working after certbot changes)

certbot commands and reference: [https://certbot.eff.org/docs/using.html#managing-certificates](https://certbot.eff.org/docs/using.html#managing-certificates)