Role Name
=========
The Ansible role allows you to deploy the `nginx+php+mysql` stack from a `docker-compose` file. The configuration files are located in the `/templates` and `/files` directories.

Requirements
------------
Use: `ansible-galaxy collection install community.docker`.
To use it in a playbook, specify: `community.docker.docker_compose_v2`.

Role Variables
--------------
```
---
# defaults file for roles/ansible_role_deploy_dockercompose
#
### Task variables ########
path_to_composefile:    "${PWD}"
path_to_Dockerfile:     "{{ path_to_composefile }}"
name_composefile:       "docker-compose.yml"
stack_name:             "deploystack"
path_to_docker:         "/usr/bin/docker"

### Containers variables #####
compose_version:        "3.8"

### Nginx container variables ######
nginx_image:            "nginx:1.25-alpine"
host_port:              "80"
nginx_port:             "80"
path_to_confignginx:    "${PWD}/nginx"
name_nginxfile:         "php.conf"

### PHP container variables ######
path_to_configphp:      "${PWD}/php"
name_phpfile:           "index.php"

### Mysql container variables ######
path_to_configmysql:      "${PWD}/mysql"
name_mysqlfile:           "my.cnf"
mysql_image:              "mysql/mysql-server:8.0"

```
Example Playbook
----------------
```
- name: Deploy Docker Compose file
  hosts: compose
  tags: compose
  roles:
    - ansible_role_deploy_dockercompose
```
