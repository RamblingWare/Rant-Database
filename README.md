# couchdb-docker

[![Build Status](https://travis-ci.org/oddoxorg/couchdb-docker.svg?branch=master)](https://travis-ci.org/oddoxorg/couchdb-docker)
[![Docker Pulls](https://img.shields.io/docker/pulls/oddoxorg/couchdb.svg)](https://hub.docker.com/r/oddoxorg/couchdb/)
[![License](https://img.shields.io/:license-apache-blue.svg)](https://github.com/oddoxorg/couchdb-docker/blob/master/LICENSE)

CouchDB Dockerfiles for Oddox

## Available Tags

- `2.1.1` - CouchDB 2.1.1 single node
- `latest` - same as above

## Features

 * Built off [apache/couchdb](https://github.com/apache/couchdb-docker) base image, which uses debian:jessie
 * Exposes port `6984` of the container
 * HTTPS by default, with a self-signed cert if none are provided
 * Docker volume `/opt/couchdb/data` for persistent data

## Usage

This project is still in development. It is not easily modifiable for "new" blogs, but stay tuned. I plan to make a self-installing version once the main features are complete.

> Note: The Official CouchDB image is located [here](https://github.com/apache/couchdb-docker). If you're looking for that instead.

### Deploy

 1. Pull [CouchDB 2.1.1](https://hub.docker.com/r/oddoxorg/couchdb/) `docker pull oddoxorg/couchdb:2.1.1`
 1. Run CouchDB `docker run -d -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=admin -p 6984:6984 --name database oddoxorg/couchdb:2.1.1`
 1. Visit `https://<container-ip>:6984/_utils/`


### Build your own

Provide your own version of the `local.ini` for your custom CouchDB config.

Example Dockerfile:

```
FROM oddoxorg/couchdb:2.1.1

COPY local.ini /opt/couchdb/etc/local.d/
COPY vm.args /opt/couchdb/etc/
COPY cert.pem /opt/couchdb/etc/cert.pem
COPY privkey.pem /opt/couchdb/etc/privkey.pem
```

and then build and run.

```
docker build -t yourname/couchdb:2.1.1 .
docker run -d -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=admin -p 6984:6984 --name database yourname/couchdb:2.1.1
```

## License

[Apache 2.0](/LICENSE)
