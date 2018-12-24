# couchdb-docker

[![Build Status](https://travis-ci.org/amdelamar/couchdb-docker.svg?branch=master)](https://travis-ci.org/amdelamar/couchdb-docker)
[![Docker Pulls](https://img.shields.io/docker/pulls/amdelamar/couchdb.svg)](https://hub.docker.com/r/amdelamar/couchdb/)
[![License](https://img.shields.io/:license-apache-blue.svg)](https://github.com/amdelamar/couchdb-docker/blob/master/LICENSE)

CouchDB Dockerfiles

> Note: The Official CouchDB image is over [here](https://github.com/apache/couchdb-docker). If you're looking for that instead.

## Available Tags

- `2.1.1` - CouchDB 2.1.1 single node
- `latest` - same as above

## Features

 * Built off [apache/couchdb](https://github.com/apache/couchdb-docker) base image, which uses debian:jessie
 * Exposes port `6984` of the container
 * HTTPS by default, with a self-signed cert if none are provided
 * Docker volume `/opt/couchdb/data` for persistent data

### Deploy

 1. Pull [CouchDB 2.1.1](https://hub.docker.com/r/amdelamar/couchdb/) `docker pull amdelamar/couchdb:2.1.1`
 1. Run CouchDB `docker run -d -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=admin -p 6984:6984 --name database oddoxorg/couchdb:2.1.1`
 1. Visit `https://<container-ip>:6984/_utils/`


### Build your own

Customize couchdb by adding your own version of the `local.ini` for your custom CouchDB config.

Example Dockerfile:

```
FROM amdelamar/couchdb:2.1.1

COPY local.ini /opt/couchdb/etc/local.d/
COPY vm.args /opt/couchdb/etc/
COPY cert.pem /opt/couchdb/etc/cert.pem
COPY privkey.pem /opt/couchdb/etc/privkey.pem
```

and then build and run.

```
docker build -t mycouchdb .

docker run -d \
  --name couchdb \
  -e COUCHDB_USER=admin \
  -e COUCHDB_PASSWORD=admin \
  -p 6984:6984 \
  mycouchdb
```

## License

[Apache 2.0](/LICENSE)
