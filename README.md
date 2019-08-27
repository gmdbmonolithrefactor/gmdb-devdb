# gmdb-devdb

## This repository will create a database sutible for the gmdb-monolith project and / or associated microservices, and will contain test data.  

### Dataload is done when creating the docker image.  Setup file is located in this repository in the file setup.sql.

### Steps to create and run the docker container...
1. Create the docker image `$ docker build -t gmdb/devdb . `
1. Deploy the new docker image to a container `$ docker run -d -p 3306:3306 --name gmdb-devdb gmdb/devdb` 
1. To list running docker containers `$ docker ps `
1. To stop the container `$ docker stop gmdb-devdb `
1. To list all containers, running or stopped `$ docker ps -a `
1. to restart this container `$ docker start gmdb-devdb `

#### Things to consider
* If you have a local mysql db on the machine, you need to change the port number (the first 3306)
* To access the database via a mysql client, use the localhost ip address found in `/etc/hosts` which is usually 127.0.0.1.  For some reason "localhost doesn't work.
* To have gmdb services access the db from the docker network, create a new bridge network in docker, `$ docker network create gmdb-bridge `, then add this network to the run command `--network gmdb-bridge `.
