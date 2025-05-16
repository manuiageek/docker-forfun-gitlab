# GitLab Docker Compose Setup

This repository contains a `docker-compose.yml` file 
to easily deploy GitLab using Docker.

## Prerequisites

* Docker and Docker Compose installed on your system.
* External volumes created before starting the containers:
  docker volume create gitlab-config
  docker volume create gitlab-logs
  docker volume create gitlab-data
  docker volume create gitlab-runner-config
* External network created before starting the containers : 
  docker network create gitlab-network
* docker compose up -d

## change root password 
docker exec -it gitlab gitlab-rake "gitlab:password:reset"
enter : root
password : theoneyouwantbuthardenoughtoguess 
retypePassword : theoneyouwantbuthardenoughtoguess

## Connection on http
Go to : http://localhost:8929/
login : root
password : the one that you have defined

## Create runner with root login
[Admin ](http://localhost:8929/admin/runners)

Create runner by replacing weird id by : 
http://localhost:8929/admin/runners/..../register

### in a powershell terminal : 
docker exec -it gitlab-runner gitlab-runner register  --url http://gitlab  --token glrt-somethingverylong

## TROUBLESHOOTING 
### gitlab-runner 

Check the Runner Configuration (config.toml)
On the server where the runner is installed, check the config.toml file (often located at /etc/gitlab-runner/config.toml or in the Docker-mounted volume /etc/gitlab-runner). Ensure that in the [runners.docker] section, you have a valid default image, for example:

in Toml file

Apply
[runners.docker]
image = "alpine:latest"
pull_policy = "if-not-present"
privileged = true
volumes = ["/var/run/docker.sock:/var/run/docker.sock", "/cache"]
If you need to modify the file:

in Shell

Apply
apk add --no-cache nano
This will allow you to edit the config.toml file using the nano editor if you are using an Alpine-based system