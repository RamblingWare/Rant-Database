# Rant-Database (CouchDB)

Blog database on CouchDB.

> NOTICE: Official CouchDB image located at https://github.com/apache/couchdb-docker

## Available tags

- `latest`, `2.0.0`: CouchDB 2.0 single node

## Features

 * Small `debian:jessie` base image
 * Auto SSL with a self-signed cert if none are provided
 * Exposes port `6984` of the container
 * Docker volume for data

## Usage

This project is still in development. It is not easily modifiable for "new" blogs, but stay tuned. I plan to make a self-installing version once the main features are complete. Essentially, this is a database for the [Rant](https://github.com/RamblingWare/Rant) backend. 

### Docker Deploy

> Coming soon...


### Build your own

Provide your own version of the `local.ini` for your custom CouchDB config.

Example Dockerfile:

```
FROM rant/database:latest

COPY local.ini /opt/couchdb/etc/local.d/
COPY cert.pem /opt/couchdb/etc/cert.pem
COPY privkey.pem /opt/couchdb/etc/privkey.pem
```

and then build and run

```
[sudo] docker build -t you/awesome-couchdb .
[sudo] docker run -d -p 6984:6984 -v ~/couchdb:/usr/local/var/lib/couchdb you/awesome-couchdb
```

## License

[Apache 2.0](/LICENSE)
