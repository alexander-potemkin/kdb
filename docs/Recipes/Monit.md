# Monit

As per Digital Ocean [page](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-monit).

Installation:

```bash
sudo apt update #AWS especially needs that
sudo apt-get install monit
sudo service monit start
sudo service monit status
```

Find and uncomment httpd part (leaving ssl part commented out) - it's required for cli interaction

```bash
sudo vi /etc/monit/monitrc #:158 in vi to jump immediately there
```

Add external check configuration file:

```bash
sudo vi /etc/monit/conf-enabled/my_check
```

For remote port configuration add the following content:

```bash
check host $MYNAME with address $DOMAIN_NAME
        if failed port 80 with protocol http and request "/" with timeout 25 seconds
then alert
```

Reload monit to appy the config file

```bash
sudo monit -t #to check if config is valid
sudo monit reload #to reload the config
sudo monit status
```

Check the logs:

```bash
sudo monit summary
tail -f /var/log/monit.log #to check the logs
```