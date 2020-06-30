# openfisca-nsw-docker

Created to build and run Openfisca API and Form Generator locally for testing.

## Build and Run

This will build and run the required containers.

Ensure ports 4000 and 4200 are not already in use.

`docker-compose up -d`

Web UI <http://127.0.0.1:4200>

API <http://127.0.0.1:4000>

## Stop

Stop containers

`docker-compose stop`

## Start

Start containers

`docker-compose start`

## Remove

Stop and remove containers and images

`docker-compose down --rmi all`

## Rebuild

To ensure servers are running the latest versions code run the following.

```bash
docker-compose down --rmi all
docker-compose up -d
```
