# Efficient Rails DevOps

Example app following the [Efficient Rails DevOps](http://www.efficientrailsdevops.com/) book by [Michael Trojanek](http://www.relativkreativ.at/about).

## Get up and running

- Clone the repo and change into the directory.
- Run `vagrant up` to start the VM.
- Use `ssh-copy-id root@192.168.253.100` using password `vagrant`, to copy your ssh public key to the VM.
- Start the playbook with `ansible-playbook -i inventories/staging site.yml`.
- Update the yum packages using `ssh root@192.168.1.100 "yum -y update"`
- `ssh root@192.168.1.100 "touch /.autorelabel && reboot"` will relabel our filesystem (which only needs to happen once).

## Important note

### Private keys

This repo contains a publically accessible private key, making the server vulnurable if you choose to use this playbook unmodified. With this in mind, if you wish to use this playbook you need replace the `authorized_keys`, `id_rsa`, and `id_rsa.pub` files in the `roles/application_user/files/` folder (following the instructions in pages *Application user* chapter) and keep them private. This repo is for reference purposes only.

### IP address

This repo is based on the IP subgroup of `192.168.253.*`. If your subgroup is different and you need to modify the IP address, you'll need to update both the `Vagrantfile` and `inventories/staging` files.

### Installing Ansible

```bash
pip install --upgrade pip
php install ansible
```

#### No Python?

If the commands above don't work, you probably don't have Python installed. The book recommends you use [pyenv](https://github.com/yyuu/pyenv) to install python, as it'll give you the ability to switch between different version, much like the benefits obtained by using rbenv.

For a a quick and dirty install process on OS X:

```bash
brew update
brew install pyenv
```

At this point it's important to note the set-up instructions provided by the installer.

```bash
pyend install 2.7.10
pyenv global 2.7.10
```
