# GitLab Docker Compose Setup

This repository contains a `docker-compose.yml` file to easily deploy GitLab using Docker.

## Prerequisites

* Docker and Docker Compose installed on your system.
* External volumes created before starting the containers:
  docker volume create gitlab-config
  docker volume create gitlab-logs
  docker volume create gitlab-data

## connect and root access
### Get root password 
Access to the bash console of the container
et show password with : 
cat /etc/gitlab/initial_root_password

### Connection
Go to : http://localhost:8929/


