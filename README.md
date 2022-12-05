# vzenix-docker-services

Enviroment for custom services build into containers docker

# Translations

* [English](https://github.com/vzenix/vzenix-docker-services/blob/main/README.md)
* [Español](https://github.com/vzenix/vzenix-docker-services/blob/main/READNE_ES.md)

# Description

This repository use the next tecnologies for maintenance of services:

* Ansible / Ansible Playbooks: Automatize install and maintenance of machines.
* Docker / Docker Compose: System for expose the services.

# Content of this repository

## ansible_vars

Varse used in the ansible playbooks

## docs

Appendeds to documentation

## 01-basics

Base install for the server, port 8080 exposed is secured by firewall, you need modify docker-compose.yaml of traefik for remove the expose 8080 port if you don't have a firewall and the machine is full exposed

Samples with ansible:

```
# Check connection
ansible all --ask-pass -m ping --limit=</ansiblle/hosts#nombre_host>

# Play the "playbook"
ansible-playbook ansible-instalacion-servidor.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

## 02-sgbd

Install SGBD used

Port 3306 exposed is secured by firewall, you need modify docker-compose.yaml of traefik for remove the expose 3306 port if you don't have a firewall and the machine is full exposed

```
# Sample for launch playbook
ansible-playbook ansible-instalacion-sgbd.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass --ask-vault-pass
```

## 03-websites

Install all public websites, require "ansible-instalacion-servidor.yaml" playbook

### 01-ansible-instalacion-www-base.yaml

Prepare system and create images of docker for host the websites

```
# Sample for launch playbook
ansible-playbook 03-websites/01-ansible-instalacion-www-base.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

### 02-ansible-instalacion-www-ping.yaml

Publish a basic website ping.vzenix.es for test

Require previous playbooks

```
# Sample for launch playbook
ansible-playbook 03-websites/02-ansible-instalacion-www-ping.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

### 03-ansible-instalacion-websites.yaml

Install or update websites services

Require previous playbooks

```
# Sample for launch playbook
ansible-playbook 03-websites/03-ansible-instalacion-websites.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

# Licence

* [Attribution 4.0 International (CC BY 4.0)](https://github.com/vzenix/vzenix-docker-services/blob/main/LICENCE.md)

# Author

* [Webpage (only spanish)](https://vzenix.es) 
