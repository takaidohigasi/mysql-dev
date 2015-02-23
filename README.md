# mysql-dev
codes for creating mysql developing environment

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

deploy virtual machine and provision

```bash
$ vagrant up
```

destroy operation is as follows (you can also use -f option to destroy)
```bash
$ vagrant halt
$ vagrant destroy
```

### Provisioning

you can also provision by following command

```bash
$ vagrant provision
```

or

```bash
$ ansible-playbook site.yml
```

you can also run script partially as follows

```bash
$ ansible-playbook site.yml -t install
$ ansible-playbook site.yml -t deploy
$ ansible-playbook site.yml -t build
```

### Operations

you can login to the deployed vm as follows

```bash
$ vagrant ssh db-server
```
