# mysql-dev
codes to create mysql develop environment

## Requirement

- Ansible
- Vagrant
 - centos box image

## Install & Setup

- Vagrant
 - http://docs.vagrantup.com/v2/installation/index.html
 - http://www.vagrantup.com/downloads

if your host needs proxy, vagrant-proxyconf plugin may be good for you.

## Usage

### Initial Settings

```bash
$ git clone https://github.com/takaidohigasi/mysql-dev.git
$ cd mysql-dev
```

please configure parameter file if you need.

```bash
$ vim roles/mysql-dev/defaults/main.yml
```

### Virtual Machine Operation

you can deploy and provision virtual machine.

```bash
$ vagrant up
```

you can destroy virtual machines as follows (you can also use -f option to destroy without confirmation)
```bash
$ vagrant halt
$ vagrant destroy
```

### Provision

you can also provision by following command.

```bash
$ vagrant provision
```

or

```bash
# this is for machine not on the virtual box.
# please do not forget to set inventory file to your configuration
$ ansible-playbook site.yml
```

you can also run script partially as follows

```bash
# install packages needed to build/run test
$ ansible-playbook site.yml -t pkg_install

# setup mysql user/group
$ ansible-playbook site.yml -t setup_user

# deploy code
$ ansible-playbook site.yml -t deploy_code

# build code, run tests, and restart mysql server
$ ansible-playbook site.yml -t build

# initialize data directory and restart mysql server
$ ansible-playbook site.yml -t install_db

# run tests
$ ansible-playbook site.yml -t test
```

### Operations

you can login to the deployed vm as follows

```bash
$ vagrant ssh db-server
```

## Features

- you can develop / debug mysql independently from you local machine.
- you don't need to care build environment because all the stuff needed is installed automatically.
- you can edit code on your host machine and run mysql on guest (code is deployed shared directory)
