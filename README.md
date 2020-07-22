# openemis-core

This public repository relates to the official OpenEMIS Docker image on [Docker Hub](https://hub.docker.com/repository/docker/openemis/core/).

## Prerequisites

    * Install [Docker](https://www.docker.com/)
    * Install [Docker Compose](https://docs.docker.com/compose/install/)

## Installation

    git clone https://github.com/OpenEMIS/core.git
    cd core
    docker-compose up -d

## Usage (docker-compose)

    * Start OpenEMIS Core at at the command prompt:
    docker-compose up -d
    
    * Login to OpenEMIS Core via a web browser:
    http://localhost:8082 (login: admin / password: demo)

    * Stop OpenEMIS Core at at the command prompt:
    docker-compose down
    
## Usage (docker)

    * Start OpenEMIS Core at at the command prompt:
    docker run --name openemis-core -p 8082:80 -e OE_HOST=... -e OE_PORT=... -e OE_USERNAME=... -e OE_PASSWORD=... -e OE_DATABASE=... -d openemis/core:latest 
    
    * Login to OpenEMIS Core via a web browser:
    http://localhost:8082 (login: admin / password: demo)

    * Stop OpenEMIS Core at at the command prompt:
    docker stop <container-id>    

## Architecture

    This repository contains a docker-compose.yaml file that is used to launch three (3) containers:
    
    # web application (openemis core)
    http://localhost:8082
    
    # database admin (phpmyadmin)
    http://localhost:8083

    # database engine (mysql)
    
    This configuration provides a number of architecture options:
    
    * one or more web application (openemis core) containers
    * database engine (mysql) as a docker container or on a different stand alone database server
    * database admin (phpmyadmin) is optional and can be removed/diabled in the docker-compose.yaml file if not required

## Configuration (docker-compose)

    It is highly recommended that you change the deafult MySQL username and password in the docker-compose.yaml:
    
      - MYSQL_ROOT_PASSWORD=...
      - MYSQL_USER=...
      - MYSQL_PASSWORD=...
    
    To run one or more web application containers (openemis core) with a database engine (mysql) 
    on a different server you will need to change the following environment variables in the
    docker-compose.yaml file:
    
    environment:
      - OE_HOST=...
      - OE_PORT=... 
      - OE_USERNAME=...
      - OE_PASSWORD=...
      - OE_DATABASE=...
      
