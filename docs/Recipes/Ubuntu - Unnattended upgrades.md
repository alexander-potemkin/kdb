# Unnattended upgrades

There is an unattended upgrades on Ubuntu/Debian, so that could be used; commands as per [the doc](https://linoxide.com/enable-automatic-updates-on-ubuntu-20-04/).

```bash
sudo apt install -y unattended-upgrades update-notifier-common apt-listchanges

```

Edit main config file

```bash
sudo systemctl status unattended-upgrades #has to be running
sudo vim /etc/apt/apt.conf.d/50unattended-upgrades
```

Default **20.04** configuration file is following:

```bash
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        "${distro_id}ESMApps:${distro_codename}-apps-security";
        "${distro_id}ESM:${distro_codename}-infra-security";
};

Unattended-Upgrade::Package-Blacklist {
};

Unattended-Upgrade::DevRelease "false";
Unattended-Upgrade::AutoFixInterruptedDpkg "false";
Unattended-Upgrade::MinimalSteps "true";
Unattended-Upgrade::Mail "mail@domain.com";
Unattended-Upgrade::MailReport "on-change";
Unattended-Upgrade::Automatic-Reboot "true";
Unattended-Upgrade::Automatic-Reboot-WithUsers "true";
Unattended-Upgrade::Automatic-Reboot-Time "03:48";
Unattended-Upgrade::SyslogEnable "true";
Unattended-Upgrade::SyslogFacility "daemon";
Unattended-Upgrade::Verbose "true";
Dpkg::Options {
   "--force-confdef";
   "--force-confold";
};
```

Make sure there is only security updates and first line (as per [this](https://askubuntu.com/questions/877999/what-is-the-meaning-of-the-different-unattended-upgradeallowed-origins)) are un-commented:

 

```bash
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
				...
```

Uncomment the following options:

```bash
Unattended-Upgrade::DevRelease "false";
Unattended-Upgrade::AutoFixInterruptedDpkg "false";
Unattended-Upgrade::MinimalSteps "true";
Unattended-Upgrade::Mail "root"; #actual e-mail, if configured with SSMTP
Unattended-Upgrade::Automatic-Reboot "true";
Unattended-Upgrade::Automatic-Reboot-WithUsers "true";
Unattended-Upgrade::Automatic-Reboot-Time "04:00";
```

and add the following lines to it (`/etc/apt/apt.conf.d/50unattended-upgrades`), as per the [doc](https://unix.stackexchange.com/questions/138751/unattended-upgrades-and-modified-configuration-files):

```bash
Dpkg::Options {
   "--force-confdef";
   "--force-confold";
};
```

Verify it's enabled:

```bash
cat /etc/apt/apt.conf.d/20auto-upgrades
```

Check how it would work:

```bash
sudo unattended-upgrades --dry-run # --debug
```

Reference: [https://habr.com/ru/company/flant/blog/330406/](https://habr.com/ru/company/flant/blog/330406/)

### Troubleshooting

```bash
/var/log/unattended-upgrades
```