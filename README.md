# skynewz.dev-server
Docker Swarm &amp; Ansible config files to automate a new server deployment

<p float="left" align="center">
  <img src="https://www.ansible.com/hubfs/Ansible-Mark-Large-RGB-Black.png" width="200" height="200">
  <img src="https://raw.githubusercontent.com/docker-library/docs/471fa6e4cb58062ccbf91afc111980f9c7004981/swarm/logo.png" width="200" height="200">
  <img src="https://docs.traefik.io/img/traefik.logo.png" width="200" height="200">
</p>

## Requirements

* [Ansible](https://www.ansible.com)
* Hosts IP address set in [hosts.ini](/hosts.ini)
* Be log as `root` to these hosts with ssh keys without password
* ⚠️ Support only Debian based distros
* Set `GANDIV5_API_KEY` into [`.env` file](roles/cluster/files/traefik/.env.example)

```bash
$ ansible-playbook -i hosts.ini site.yml
```

## Details

- Install
  * `curl`
  * `vim`
  * `htop`
  * `sudo`
  * `fail2ban`
  * some Python modules required by Ansible
- Install Docker from [script](https://get.docker.com)
- Create new user :
  * `quentin`
  * with encrypted password
  * `sudo` rights
  * `docker`rights
  * with my public key
- Disable `PermitRootLogin`, `PermitEmptyPasswords`, `PasswordAuthentication`
- Delete `root` password, only `sudo`
- Configure `sshd` jail for `fail2ban`
- Configure timezone
- Install docker swarm cluster on given managers and workers
- 🚸 Create directories required my stacks
- 🚸 Create needed network for [Traefik](http://traefik.io)
- 🚸 Deploy all my stacks to this cluster
- 🚸 Add personal `crontabs`