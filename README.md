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

### in a powershell : 
docker exec -it gitlab-runner gitlab-runner register



