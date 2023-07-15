# vzenix-docker-services

Enviroment for custom services build into containers docker

* **Caution:** docker-compose up is commented in ansible playbooks, uncomment its if don't want do it manually

# Translations

* [English](https://github.com/vzenix/vzenix-docker-services/blob/main/README.md)
* [Español](https://github.com/vzenix/vzenix-docker-services/blob/main/README_ES.md)

# Description

This repository use the next tecnologies for maintenance of services:

* Ansible / Ansible Playbooks: Automatize install and maintenance of machines.
* Docker / Docker Compose: System for expose the services.

# Content of this repository

## ansible_vars

Vars used in the ansible playbooks

## docs

Appendeds to documentation

## 01-basics

Base install for the server, port 8080 exposed is secured by firewall, you need modify docker-compose.yaml of traefik for remove the expose 8080 port if you don't have a firewall and the machine is full exposed

Samples with ansible:

```
# Check connection
ansible all --ask-pass -m ping --limit=</ansible/hosts#nombre_host>

# Play the "playbook"
ansible-playbook 01-basics/01-ansible-server-install.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
ansible-playbook 01-basics/02-ansible-docker-network.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
ansible-playbook 01-basics/03-ansible-proxy.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
```

## 02-sgbd

Install SGBD used

Port 3306 exposed is secured by firewall, you need modify docker-compose.yaml of traefik for remove the expose 3306 port if you don't have a firewall and the machine is full exposed

Remeber set password in ansinble_vars/vars.yaml file

```
# Sample for launch playbook
ansible-playbook 02-sgbd/01-ansible-sgbd-mariadb.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
```

## 03-websites

Install all public websites, require "ansible-instalacion-servidor.yaml" playbook

### 01-ansible-instalacion-www-base.yaml

Prepare system and create images of docker for host the websites

```
# Sample for launch playbook
ansible-playbook 03-websites/01-ansible-instalacion-www-base.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
```

### 02-ansible-instalacion-www-ping.yaml

Publish a basic website ping.vzenix.es for test

Require previous playbooks

```
# Sample for launch playbook
ansible-playbook 03-websites/02-ansible-instalacion-www-ping.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
```

### 03-ansible-instalacion-websites.yaml

Install or update websites services

Require previous playbooks

```
# Sample for launch playbook
ansible-playbook 03-websites/01-ansible-install-www-base.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
ansible-playbook 03-websites/02-ansible-install-www-ping.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
ansible-playbook 03-websites/03-ansible-install-websites.yaml --limit=</ansible/hosts#nombre_host> --ask-pass
```

# Licence

* [Attribution 4.0 International (CC BY 4.0)](https://github.com/vzenix/vzenix-docker-services/blob/main/LICENCE.md)

# Author

* [Webpage (only spanish)](https://vzenix.es) 
