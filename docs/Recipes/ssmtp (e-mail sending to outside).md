# ssmtp (e-mail sending to outside)

<aside>
💡 Note, that ssmtp package is unmaintained; Debian offers [msmtp](https://wiki.debian.org/msmtp) as a replacement.

</aside>

As per the [ArchLinux doc](https://wiki.archlinux.org/index.php?title=SSMTP), [systorials doc](https://www.systutorials.com/docs/linux/man/5-ssmtp.conf/) + not touched example [1](https://support.cloud.engineyard.com/hc/en-us/articles/205407478-Set-Up-SSMTP-for-Mail-Relay-to-AuthSMTP);  

```bash
sudo apt -y install ssmtp
```

`sudo vi /etc/ssmtp/ssmtp.conf` to look like that:

```bash
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=mailbox@domain.com

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail.domain.com:587

# Where will the mail seem to come from?
rewriteDomain=domain.com

# The full hostname
hostname=MYSERVER

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=NO

AuthUser=notifier@domain.com
AuthPass=password
AuthMethod=
UseSTARTTLS=YES
```

`sudo vi /etc/ssmtp/revaliases` to:

```bash
root:notifier@domain.com:mail.domain.com:587
admin:notifier@domain.com:mail.domain.com:587
```

Then try out things:

```bash
echo -e 'Subject: test\n\nTesting ssmtp' | sendmail -v admin@domain.com
```

Log files are at `/var/log/mail*`