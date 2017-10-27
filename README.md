# Rant-Database (CouchDB)

[![Build Status](https://travis-ci.org/RamblingWare/Rant-Database.svg?branch=master)](https://travis-ci.org/RamblingWare/Rant-Database)
[![Docker Pulls](https://img.shields.io/docker/pulls/rant/couchdb.svg)](https://hub.docker.com/r/rant/couchdb/)
[![License](https://img.shields.io/:license-apache-blue.svg)](https://github.com/RamblingWare/Rant-Database/blob/master/LICENSE)

Blog database for Rant.

## Available Tags

- `2.1.0` - CouchDB 2.1.0 single node
- `latest` - same as above

## Features

 * Built off [apache/couchdb](https://github.com/apache/couchdb-docker) base image, which uses debian:jessie 
 * Exposes port `6984` of the container
 * HTTPS by default, with a self-signed cert if none are provided
 * Docker volume `/opt/couchdb/data` for persistent data

## Usage

This project is still in development. It is not easily modifiable for "new" blogs, but stay tuned. I plan to make a self-installing version once the main features are complete. Essentially, this is a database for the [Rant](https://github.com/RamblingWare/Rant) webapp.

> Note: The Official CouchDB image is located [here](https://github.com/apache/couchdb-docker). If you're looking for that instead.

### Deploy

 1. Pull [CouchDB 2.1.0](https://hub.docker.com/r/rant/couchdb/) `docker pull rant/couchdb:2.1.0`
 1. Run CouchDB `docker run -d -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=admin -p 6984:6984 --name database rant/couchdb:2.1.0`
 1. Visit `https://<container-ip>:6984/_utils/`


### Build your own

Provide your own version of the `local.ini` for your custom CouchDB config.

Example Dockerfile:

```
FROM rant/couchdb:2.1.0

COPY local.ini /opt/couchdb/etc/local.d/
COPY vm.args /opt/couchdb/etc/
COPY cert.pem /opt/couchdb/etc/cert.pem
COPY privkey.pem /opt/couchdb/etc/privkey.pem
```

and then build and run.

```
docker build -t yourname/couchdb:2.1.0 .
docker run -d -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=admin -p 6984:6984 --name database yourname/couchdb:2.1.0
```

## License

[Apache 2.0](/LICENSE)
