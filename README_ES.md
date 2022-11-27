# vzenix-docker-services

Entorno para servicios propios construidos en contenedores docker

# Traducciones

* [English](https://github.com/vzenix/vzenix-docker-services/blob/main/README.md)
* [Español](https://github.com/vzenix/vzenix-docker-services/blob/main/READNE_ES.md)

# Descripción

Se usan las siguientes tecnologías para mantenimiento de los servicios:

* Ansible / Ansible Playbooks: Automatización en la instalación/mantenimiento de servidores
* Docker / Docker Compose: Sistema para exponer los diferentes servicios

# Contenido del repositorio

## docs

Documentación anexa

## 01-basics

Instalación base del servidor, el puerto 8080 se securiza en el cortafuegos, modificar docker-compose.yaml de traefik para no exponer esto en caso de ser un servidor compeltamente público

```
# Verificar conexión
ansible all --ask-pass -m ping --limit=</ansiblle/hosts#nombre_host>

# Lanzar playbook (--verbose más información)
ansible-playbook ansible-instalacion-servidor.yaml --limit=</ansiblle/hosts#nombre_host> --ask-pass
```

# Licencia

* [Attribution 4.0 International (CC BY 4.0)](https://github.com/vzenix/vzenix-docker-services/blob/main/LICENCE.md)

# Autor

* [Web (solo en castellano)](https://vzenix.es) 
