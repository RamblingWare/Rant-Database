# Rant-Database (CouchDB)

Blog database on CouchDB.

> NOTICE: Official CouchDB image located [here](https://github.com/apache/couchdb-docker).

## Available tags

- `latest`, `2.1.0`: CouchDB 2.1.0 single node

## Features

 * Small `debian:jessie` base image
 * Auto SSL with a self-signed cert if none are provided
 * Exposes port `6984` of the container
 * Docker volume for data `/opt/couchdb/data`

## Usage

This project is still in development. It is not easily modifiable for "new" blogs, but stay tuned. I plan to make a self-installing version once the main features are complete. Essentially, this is a database for the [Rant](https://github.com/RamblingWare/Rant) backend. 

### Docker Deploy

```
docker pull rant/couchdb:2.1.0
docker run -d -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=admin -p 6984:6984 --name database rant/couchdb:2.1.0
```


### Build your own

Provide your own version of the `local.ini` for your custom CouchDB config.

Example Dockerfile:

```
FROM rant/couchdb:2.1.0

COPY local.ini /opt/couchdb/etc/local.d/
COPY cert.pem /opt/couchdb/etc/cert.pem
COPY privkey.pem /opt/couchdb/etc/privkey.pem
```

and then build and run.

```
docker build -t rant/couchdb:2.1.0 .
docker run -d -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=admin -p 6984:6984 --name database rant/couchdb:2.1.0
```

## License

[Apache 2.0](/LICENSE)
