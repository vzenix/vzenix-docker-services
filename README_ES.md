# vzenix-docker-services

Entorno para servicios propios construidos en contenedores docker

# Traducciones

* [English](https://github.com/vzenix/vzenix-docker-services/blob/main/README.md)
* [Español](https://github.com/vzenix/vzenix-docker-services/blob/main/README_ES.md)

# Descripción

Se usan las siguientes tecnologías para mantenimiento de los servicios:

* Ansible / Ansible Playbooks: Automatización en la instalación/mantenimiento de servidores
* Docker / Docker Compose: Sistema para exponer los diferentes servicios

# Contenido

## docs

Documentación anexa

## 01-basics

Instalación base del servidor, el puerto 8080 se securiza en el cortafuegos, modificar docker-compose.yaml de traefik para no exponer esto en caso de ser un servidor compeltamente público

```
# Verificar conexión
ansible all --ask-pass -m ping --limit=</ansiblle/hosts#nombre_host>

# Lanzar playbook (--verbose más información)
ansible-playbook 02-sgbd/ansible-instalacion-servidor.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

## 02-sgbd

Instalación de los SGBD usados

El puerto 3306 se securiza en el cortafuegos, modificar docker-compose.yaml de traefik para no exponer esto en caso de ser un servidor compeltamente público

```
# Ejemplo de comando para lanzar el playbook
ansible-playbook 02-sgbd/ansible-instalacion-sgbd.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass --ask-vault-pass
```

## 03-websites

Instala todos los portales webs públicos, requiere el playbook "ansible-instalacion-servidor.yaml"

### 01-ansible-instalacion-www-base.yaml

Prepara el sistema y crea las imágenes de docker para hospedar los portales web

```
# Ejemplo de comando para lanzar el playbook
ansible-playbook 03-websites/01-ansible-instalacion-www-base.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

### 02-ansible-instalacion-www-ping.yaml

Publica un portal básico https://ping.vzenix.es para pruebas

```
# Ejemplo de comando para lanzar el playbook
ansible-playbook 03-websites/02-ansible-instalacion-www-ping.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

### 03-ansible-instalacion-websites.yaml

Instala o actualiza los portales webs

```
# Ejemplo de comando para lanzar el playbook
ansible-playbook 03-websites/03-ansible-instalacion-websites.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

# Licencia

* [Attribution 4.0 International (CC BY 4.0)](https://github.com/vzenix/vzenix-docker-services/blob/main/LICENCE.md)

# Autor

* [Web (solo en castellano)](https://vzenix.es) 
