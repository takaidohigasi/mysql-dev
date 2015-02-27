# mysql-dev
codes to create mysql develop environment

## Requirement

- ansible
- vagrant
 - centos box image

## Install & Setup

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
$ ansible-playbook site.yml
```

you can also run script partially as follows

```bash
$ ansible-playbook site.yml -t pkg_install
$ ansible-playbook site.yml -t setup_user
$ ansible-playbook site.yml -t deploy_code
$ ansible-playbook site.yml -t build
$ ansible-playbook site.yml -t install_db
```

### Operations

you can login to the deployed vm as follows

```bash
$ vagrant ssh db-server
```

mysql code is deployed for /vagrant directory by default which is shared between host and guest.
you can modify code on the host.
