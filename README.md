# Vagrant VM of a Rails application with multiple instances

Using ansible provisioning.

# Prepare for installing
Add ssh key to ssh-agent. It's used for code fetching from the github
```shell
ssh-add -K <path to the key> # on Mac OS
```

Install [vagran-hosts](https://github.com/oscar-stack/vagrant-hosts) plugin for hosts discovery

```shell
vagrant plugin install vagrant-hosts
```

# Single command installing

Now we are ready to go

```shell
vagrant up --provision
```

open `192.168.0.6` in host browser
