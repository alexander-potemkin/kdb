# Mattermost + Audio & Video calls + S3

**MinIO** is to be installed from CapRover - configured via Web interface, requires HTTPS & domain name. Default region is *us-east-1.*

**Jitsi** from CapRover as well. No configuration needed, except for HTTPS and forcing HTTPS everywhere.

If a connection error will occur, `ENABLE_XMPP_WEBSOCKET=0` has to be added to the environment variables (fixes websocket error in console).

**Mattermost** comes from Cloudron (free plan), at System Console enable Plugins, find and enable Jitsi. Make sure you put Jitsi url in HTTP**S** (otherwise it generates insecure frame connection at console).
Enable embed Jitsi video inside option, to keep things happening purely inside Jitsi.

### Troubleshooting

For **Jitsi** troubleshooting open console (Alt + Cmd + I on Chrome on Mac) and check for the error message.

**Mattermost** has server logs (available from the System Console as well).

No **MinIO** troubleshooting was done, but [S3 things](S3%20things.md) could be of help.

### Change channel to public

```bash
sudo -u cloudron /app/code/bin/mattermost --config=/app/data/config.json channel modify $teamid:$channelname --username $username --public
```

Other command line arguments: [https://docs.mattermost.com/administration/command-line-tools.html#mattermost-channel-modify](https://docs.mattermost.com/administration/command-line-tools.html#mattermost-channel-modify)


# MatterMost tips and tricks

To add repository to the channel (after all of the preparations has been made).

```bash
/github subscriptions add Potemkin-Co/repo_name pulls,pushes,creates,deletes,pull_reviews
```