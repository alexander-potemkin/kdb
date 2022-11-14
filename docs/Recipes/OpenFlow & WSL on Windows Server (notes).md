- choose Windows with containers (enable key to use to decrypt the Administrator's password) on metal 
- Install security updates
- install https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
- Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
- wsl --install # this might fail, it's Ok, if next command is successfull
- wsl --set-default-version 2
- wsl --list --online # to view the distros available
- wsl --install -d Ubuntu-18.04
- apply DNS solution as per [this article](https://superuser.com/questions/1533291/how-do-i-change-the-dns-settings-for-wsl2)
git clone https://github.com/open-rpa/docker.git
cd docker
docker-compose -f docker-compose-traefik.yml -p openrpa up -d
- open http://localhost.openiap.io/#/Login and login with the name that you want to be an admin, each nodered started inside openflow, will be listening at username.localhost.openiap.io (as per [doc](https://github.com/open-rpa/docker))
- follow the instruction at https://docs.openiap.io/openflow.html

Articles:
- https://techcommunity.microsoft.com/t5/itops-talk-blog/wsl2-now-available-on-windows-server-2022/ba-p/3447570
- https://stackoverflow.com/questions/46248193/how-can-i-run-docker-in-a-aws-windows-server-environment
- https://stackoverflow.com/questions/71379361/how-can-i-run-docker-desktop-in-an-aws-ec2-windows-server-environment
- https://docs.microsoft.com/en-us/windows/wsl/install-on-server


# AWS steps

* choose Windows with containers (enable key to use to decrypt the Administrator's password) on metal
* Install security updates
* Start PowerShell

Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

install [https://wslstorestorage.blob.core.windows.net/wslblob/wsl\_update\_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
```
wsl --install # this might fail, it's Ok, if next command is successfull
wsl --set-default-version 2
wsl --list --online
wsl --install -d Ubuntu-18.04
```

 for a Windows 10 or Windows 2022 server - apply DNS solution as per [this article](https://superuser.com/questions/1533291/how-do-i-change-the-dns-settings-for-wsl2)

`wget -O - [https://raw.githubusercontent.com/Potemkin-Co/quicky/main/docker\_ubuntu.sh](https://raw.githubusercontent.com/Potemkin-Co/quicky/main/docker_ubuntu.sh) | bash`

this can fail during inability to choose 'yes' or 'no' - in this case \`wsl --terminate Ubuntu-18.04\` followed by \`wsl -d Ubuntu-18.04\` and \`sudo dpkg --configure -a\`, followed by running the command again

```
wget [https://raw.githubusercontent.com/alexander-potemkin/quickies/main/nonprod-openrpa-openflow.yml](https://raw.githubusercontent.com/alexander-potemkin/quickies-dockers/main/nonprod-openrpa-openflow.yml)
sudo service docker start
sudo curl -SL [https://github.com/docker/compose/releases/download/v2.6.1/docker-compose-linux-x86\_64](https://github.com/docker/compose/releases/download/v2.6.1/docker-compose-linux-x86_64) -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
docker-compose --version
sudo docker-compose -f nonprod-openrpa-openflow.yml -p openrpa up -d
```
open [http://localhost.openiap.io/#/Login](http://localhost.openiap.io/#/Login) and login with the name that you want to be an admin, each nodered started inside openflow, will be listening at [username.localhost.openiap.io](http://username.localhost.openiap.io) (as per [doc](https://github.com/open-rpa/docker))

at Node-Red settings - mark auto-create check box to enable it the auto-start

  

`sudo vi /etc/wsl.conf` - add at `[boot]` section
`command="service docker start"`

right click on Windows icon -> Run  
enter \`shell:startup\`  
choose shortcut -> enter \`wsl -d Ubuntu-18.04\` in the shortcut

Starting OpenRPA

using taskmanager start OpenRPA installation file as an administrator

$user\\Documents\\OpenRPA\\settings.json - change app to localhost and wss to ws - make sure the file is saved!!

**Notes**

\- docker-compose v1 man: [https://docs.docker.com/engine/reference/commandline/compose\_up/](https://docs.docker.com/engine/reference/commandline/compose_up/)

\- if the Docker won't start automatically, add WSL to the auto-start: [https://www.reddit.com/r/bashonubuntuonwindows/comments/rb03b7/how\_to\_start\_wsl2\_automatically\_on\_boot\_in/](https://www.reddit.com/r/bashonubuntuonwindows/comments/rb03b7/how_to_start_wsl2_automatically_on_boot_in/)

[https://superuser.com/questions/1112007/how-to-run-ubuntu-service-on-windows-at-startup](https://superuser.com/questions/1112007/how-to-run-ubuntu-service-on-windows-at-startup)