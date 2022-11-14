# Ubuntu

### enable journald size limit

as per [this article](https://askubuntu.com/questions/1012912/systemd-logs-journalctl-are-too-large-and-slow)

```bash
journalctl --disk-usage # to check the usage

journalctl --vacuum-size=200M #to clean things up

grep SystemMaxUse /etc/systemd/journald.conf  #parameter to support logs
SystemMaxUse=50M
```

### alternative for cron - systemd

from [here](https://linuxconfig.org/how-to-schedule-tasks-with-systemd-timers-in-linux)

```bash
systemctl list-timers
```

### Disable IPv6 in Ubuntu

`vi sysctl.conf`

```bash
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
```

followed by `sysctl -p` , as per this [page](https://www.digitalocean.com/community/questions/how-do-i-disable-ipv6-on-ubuntu-20-04).

### Install Node.JS 16

```bash
wget -O - https://raw.githubusercontent.com/alexander-potemkin/quickies/main/nodejs16.sh | bash
```

### Laptop battery status

```bash
upower -e
upower -i <battery_path>

cd /sys/class/power_supply/BAT0
ls #enjoy the choice
cat cycle_count
```

### Adding Swap file

Adding swap file to the system (on the root filesystem), as per [this article](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04).

```bash
sudo swapon --show #shows if swap is available and used
free --giga -h #shows the RAM
sudo fallocate -l 1G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo swapon --show
```

Then add the following line into `/etc/fstab`

```bash
/swapfile    none    swap    sw    0   0
```

## Shell constructs

```bash
$(output=($(host $(hostname)));echo ${output[3]}) #give external IP address of the machine configured hostname

$ echo $(output=($(host $(hostname)));echo ${output[3]}) 
IP

$ hostname
domain.com

$ host domain.com
domain.com has address IP

$ echo $(output=($(host $(hostname)));echo ${output[3]})
IP
```

### Lifehacks

How to download `dpkg` files for the computer, that doesn't have internet connection (as per this [article](https://stackoverflow.com/a/26239050/2188026)) - on the 'victim' machine do:

```bash
apt-get --print-uris --yes install <my_package_name> | grep ^\' | cut -d\' -f2 >downloads.list
```

Then on the machine having internet access:

```bash
wget --input-file myurilist
```

`fdisk -l` and `mount /dev/sda1 /mnt` are other useful commands in command line interface without GUI.

Search for the file in all of the packages (you have the file and don't know which one you need):

```bash
apt-file search file -> search for the package where this file is in
```

### One liners

```bash
ls -l /var/run/reboot-required #check if reboot is required, after the apt upgrade
```

```bash
sudo update-alternatives --config editor #change default editor
```

```bash
sudo dpkg-reconfigure tzdata #change timezone
```

```bash
sudo netstat -tulpn #show open ports
```

```bash
systemd-resolve --status #show DNS configuration
```

```bash
#fixing GPG “NO_PUBKEY” error
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys MISSING_KEY
```

**Creating users**

```bash
sudo adduser $UserName
sudo usermod -aG sudo $UserName #add user to sudo group, to enable passwordless sudo

rsync --archive --chown=$UserName:$UserName ~/.ssh /home/$UserName #copy SSH keys
# OR
sudo su - $UserName
mkdir .ssh && cd .ssh
touch authorized_keys && vi authorized_keys && chmod 600 authorized_keys
```

```bash
lsof -nP -iTCP -sTCP:LISTEN #MacOS X - find which apps listen which port
```

### Hostname change (Ubuntu)

```bash
sudo hostnamectl set-hostname $NewHostname
sudo vi /etc/hosts
hostnamectl # to verify
```

**Mount another disk on Ubuntu (useful for recovery)**

```bash
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
sudo mount /dev/... /mnt
```