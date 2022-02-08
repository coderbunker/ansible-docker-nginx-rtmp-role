nginx-rtmp Docker
=========

Ce rôle sert à déployer/remettre en état un serveur nginx-rtmp via Docker Compose. L'image utilisée est celle-ci : https://hub.docker.com/r/alqutami/rtmp-hls

Requirements
------------

### Matériel
* Minimum : 
* Recommandé : 

### Système d'exploitation
* Ubuntu 20.04 (seul SE testé)

### Docker, Docker Compose, certbot, nginx
* IMPORTANT : Docker, Docker Compose, certbot et nginx NE SONT PAS installés par le rôle
* NOTE : Les paquets .deb disponibles dans Ubuntu 20.04 (universe) sont suffisants

Role Variables
--------------

### defaults/main.yml

Les valeurs par défaut dans defaults/main.yml qu'il est normal d'adapter sont l'utilisateur unix qui exécute Docker et Docker Compose et le nom de l'hôte qui est configuré pour nginx. Vous pouvez les modifier directement dans main.yml ou mieux encore les supplanter ailleurs (par exemple dans votre playbook site.yml).

Dependencies
------------

Aucune dépendance à d'autres rôles Ansible.

Example Playbook
----------------

```
- name: "Deployer un serveur nginx-rtmp via Docker Compose"
  hosts: 
    - all
  vars:
    # Supplanter ici les variables du role au besoin

  pre_tasks:
    - name: "Installer Docker, Docker Compose"
      apt:
        name: docker.io, docker-compose
        state: present
      become: yes
  roles:
    - { role: ansible-docker-nginx-rtmp-role, tags: "nginx-rtmp" }
```

License
-------

GPL-3.0-only

Author Information
------------------

Mathieu GP, admin. sys. pour Coderbunker
