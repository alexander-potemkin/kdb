# GitLab

# GitLab → GitHub sync

1. Don’t rely on SSH sync - it doesn’t seem to work, as per the [documentation](https://docs.gitlab.com/ee/user/project/repository/mirror/push.html#set-up-a-push-mirror-from-gitlab-to-github) and an [issue on the forum](https://forum.gitlab.com/t/issues-creating-push-mirror-to-github/61766/3) raised.
2. So, go the repository settings → Repository → Mirroring repository
3. Enter **HTTPS** URL of the github repository, enter your [PAT](https://github.com/settings/tokens) from GitHub as a password, click ‘Mirror repository’ and then ‘sync’ icon.

# GitLab → GitLab sync

1. On the source repository settings → Repository → Mirroring repository
2. Add mirror, copy public key
3. On the destination add this key to the repository settings → Repository → Deploy Keys, with an option to allow wrie

# DRAFTS on self hosted install & runners

<aside>
✍🏻 DON'T USE DPKG, INSTALL BINARY file as per GitLab instruction.
dpkg doesn't start service

</aside>

Take instruction from Settings → CI/CD → Show Runner installation instruction.

Install Docker:

[Docker (on Ubuntu)](Docker%20(on%20Ubuntu).md)

Then add gitlab-runner to the docker group:

```bash
sudo usermod -aG docker gitlab-runner
```

Return back to registration command from GitLab Web page and fill in the questionnaire as per the specific case you have.

If runner won't be picked up, execute the following command here:

```bash
sudo gitlab-runner verify 
```

### LEGACY THINGS GOES BELOW

TODO: transform into the troubleshooting steps

On executor choose docker (as per [doc](https://docs.gitlab.com/runner/executors/))

```bash
gitlab-runner unregister --all-runners
gitlab-runner unregister --url http://gitlab.example.com/ --token t0k3n
```

### Setting up Runner

Register it (as per [doc](https://docs.gitlab.com/runner/register/))

```bash
sudo gitlab-runner register
sudo gitlab-runner verify #to connect the runner with GitLab
```

### Runner in Docker [DOESN'T WORK]

Needs docker executor with socket bypass / forward.

Register it (as per [doc](https://docs.gitlab.com/runner/register/))

```bash
sudo docker run --rm -it -v /srv/gitlab-runner/config:/etc/gitlab-runner gitlab/gitlab-runner register
```

Verify if things are ok:

```bash
sudo docker run --rm -it -v /srv/gitlab-runner/config:/etc/gitlab-runner gitlab/gitlab-runner --debug verify
```

Remove old / not required runners registration from the local machine:

```bash
sudo docker run --rm -it -v /srv/gitlab-runner/config:/etc/gitlab-runner gitlab/gitlab-runner --debug verify --delete
```