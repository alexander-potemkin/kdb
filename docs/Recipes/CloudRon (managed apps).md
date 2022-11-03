### To get embedded turn credentials
`env | grep CLOUDRON_TURN` inside TURN enabled app, as per this [forum thread](https://forum.cloudron.io/topic/2467/how-to-use-cloudron-s-coturn-server-with-non-cloudron-apps). 

### Install
```bash
wget https://cloudron.io/cloudron-setup --no-check-certificate && chmod +x ./cloudron-setup && sudo ./cloudron-setup
```

It will take some time (10-30 minutes, depending on the server speed).

Then process to the [https://server_ip](https://server_ip) for further web based setup (in Chrome type `thisisunsafe` to proceed through SSL certificate warning).

### For manual DNS management

Manual DNS management is not a problem - **use wildcard**  - it requires 3 things to do/consider:

1. Create A type record for * and for [hostname.domain.com](http://hostname.domain.com) to IP address, which usually requires hostname ⇒ IP address type record (without domain.com)
2. Creating same kind of record with `my` at the beggining: `my.hostname` ⇒ IP address
3. Direct A record for every app that is installed (the app will give a hint)

## Mail setup

E-mail relay is required to deliver mails to Google & Microsoft. From the [forum threads](https://forum.cloudron.io/topic/5268/e-mail-relay-service-recommendation/2) it seems, that [ElasticMail](https://elasticemail.com/email-api-pricing) and [PostMark](https://postmarkapp.com/pricing) are the best options. Both configured via [Web UI](https://docs.cloudron.io/email/#relay-outbound-mails) for e-mail relay.

## Change linked account for the instance

As per [the doc](https://docs.cloudron.io/appstore/#change-associated-account).

ssh to the server, execute:

```bash
mysql -uroot -ppassword -e "DELETE FROM box.settings WHERE name='cloudron_token';"
```

Then login to the AppStore under the account, that needs to be linked. That's it.

# Automated HTTPS certificated update

As per this [forum thread](https://forum.cloudron.io/topic/5648/update-domain-names-with-the-cli-yet-another-topic/11).

```bash
#!/bin/bash
dns_host_name='domain.com'
token='' #get it from profile page

set +e
set +x

sudo netstat -nr 
sudo route add default gw `sipcalc -I ens3 -i | grep "Usable range" | cut -d "-" -f 2 | xargs` ens3
sudo route del default gw 192.168.168.1 ens4
sudo netstat -nr

curl -k -X POST -H 'Content-Type: application/json' -H "authorization: Bearer $token" --data '{}' https://$dns_host_name/api/v1/cloudron/renew_certs
echo "You can check the status of the task at https://$dns_host_name/logs.html?taskId=$task_id_from_above"
sleep 180

sudo route add default gw 192.168.168.1 ens4
sudo route del default gw `sipcalc -I ens3 -i | grep "Usable range" | cut -d "-" -f 2 | xargs` ens3
sudo netstat -nr
```

Could add it to the cron monitoring

```bash
@weekly https_certs_update.sh >> https_certs_update.log 2>&1
```

### Troubleshooting

Login failures are in the dovecot logs. You can see "/run/dovecot/dovecot.log" in the mail container (docker exec -ti mail /bin/bash). This is currently not exposed in the Cloudron dashboard. In any case, it will only report if login worked or not, it will hard to make out why it failed.

### Remove 2FA for admin user

As per the [doc](https://forum.cloudron.io/topic/5794/how-to-reset-2fa-for-admin): ssh to the server and execute:

```bash
#display the current status
mysql -uroot -ppassword -e "select username, email, resetToken, twoFactorAuthenticationSecret, twoFactorAuthenticationEnabled from box.users";

#reset the 2FA
mysql -uroot -ppassword -e "UPDATE box.users set twoFactorAuthenticationEnabled=0 where username='t.test'";
```

Two factor auth reset for admin: [http://forum.cloudron.io/topic/5794/how-to-reset-2fa-for-admin](http://forum.cloudron.io/topic/5794/how-to-reset-2fa-for-admin)

# How to send e-mail via CloudRon

```bash
docker inspect --format '{{ .NetworkSettings.Networks.cloudron.IPAddress }}' mail #gives IP address
docker inspect --format '{{ .Config.Env }}' mail | tr ' ' '\n' | grep CLOUDRON_RELAY_TOKEN | sed 's/^.*=//' #gives token

```

```bash
swaks -s `docker inspect --format '{{ .NetworkSettings.Networks.cloudron.IPAddress }}' mail` -p 2525 --au user@domain.com --ap `docker inspect --format '{{ .Config.Env }}' mail | tr ' ' '\n' | grep CLOUDRON_RELAY_TOKEN | sed 's/^.*=//'` -f 'user@domain.com' -t 'user@domain.com' --h-Subject "Test mail"
```


### Command line app install
as per https://docs.cloudron.io/packaging/tutorial/#update

```bash
npx cloudron login my.domain.com
wget https://raw.githubusercontent.com/GetZenDev/build-openfire-docker/main/CloudronManifest.json
npx cloudron install --image getzendev/openfire:latest
```

to update:
```bash
export DOMAIN_NAME=mydomain.com
wget https://raw.githubusercontent.com/GetZenDev/build-openfire-docker/main/CloudronManifest.json
npx cloudron status --app $DOMAIN_NAME
npx cloudron update --image getzendev/openfire:latest --app $DOMAIN_NAME
npx cloudron status --app $DOMAIN_NAME
```
