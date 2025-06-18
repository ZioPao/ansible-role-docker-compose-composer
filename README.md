ansible-role-docker-compose-composer
====================================

An Ansible role that manages Docker Compose applications by handling the composition, deployment, and lifecycle management of multi-container Docker applications using docker-compose files.

Requirements
------------

- Docker must be installed on the target hosts
- Docker Compose must be installed on the target hosts
- Python docker library (can be installed via pip: `docker`)
- Sufficient permissions to manage Docker containers and volumes

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Local directory where compose directories are stored
docker_compose_composer_local_services_path: "services"

# Directory where templatized compose and its other files are going to be placed
docker_compose_composer_dest_path: "~"

# Directory where appdata is stored
docker_compose_composer_appdata_path: "~"

# UID for dest path
docker_compose_composer_uid: 1000

# GID for dest path
docker_compose_composer_gid: 1000
```

Example Playbook
----------------

Here's an example of how to use this role:

```yaml
- hosts: servers
  roles:
    - role: ansible-role-docker-compose-composer
      vars:
        docker_compose_composer_local_services_path: "services"
        docker_compose_composer_uid: 1000
        docker_compose_composer_gid: 1000
        docker_compose_composer_dest_path: "~"
        docker_compose_composer_appdata_path: "~"
```

What This Role Does
-------------------

This role performs the following tasks:

1. **Creates project directory**: Sets up the specified directory structure for the Docker Compose project in the destination
2. **Generates docker-compose.yml**: Creates the docker-compose file from the provided definition, based on environment variables using jninja2
3. **Manages environment files**: Handles environment variable files if specified
4. **Starts services**: Manages the lifecycle of Docker Compose services

License
-------

GPL-2.0-or-later

