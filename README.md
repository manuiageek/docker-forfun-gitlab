# GitLab Docker Compose Setup

This repository contains a `docker-compose.yml` file to easily deploy GitLab using Docker.

## Prerequisites

* Docker and Docker Compose installed on your system.
* External volumes created before starting the containers:
  docker volume create gitlab-config
  docker volume create gitlab-logs
  docker volume create gitlab-data

