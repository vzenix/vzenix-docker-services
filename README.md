# vzenix-docker-services

Enviroment for custom services build into containers docker

# Translations

* [English](https://github.com/vzenix/vzenix-docker-services/blob/main/README.md)
* [Español](https://github.com/vzenix/vzenix-docker-services/blob/main/READNE_ES.md)

# Description

This repository use the next tecnologies for maintenance of services:

* Ansible / Ansible Playbooks: Automatize install and maintenance of machines.
* Docker / Docker Compose: System for expose the services.

# Contenido del repositorio

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

Install of SGBD used

Port 3306 exposed is secured by firewall, you need modify docker-compose.yaml of traefik for remove the expose 3306 port if you don't have a firewall and the machine is full exposed

```
# Sample for launch playbook
ansible-playbook ansible-instalacion-sgbd.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass --ask-vault-pass
```

# Licence

* [Attribution 4.0 International (CC BY 4.0)](https://github.com/vzenix/vzenix-docker-services/blob/main/LICENCE.md)

# Author

* [Webpage (only spanish)](https://vzenix.es) 
