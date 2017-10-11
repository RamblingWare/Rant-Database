# Rant-Database (CouchDB)

Blog database on CouchDB.

NOTICE: Official CouchDB image located at https://github.com/apache/couchdb-docker
If you're looking for a CouchDB with SSL support you can check out [klaemo/couchdb-ssl](https://index.docker.io/u/klaemo/couchdb-ssl/)

- Version (stable): `CouchDB 2.0.0`, `Erlang 17.3`

## Available tags

- `latest`, `2.0.0`: CouchDB 2.0 single node

## Features

 * Built on top of the solid and small `debian:jessie` base image
 * Exposes CouchDB on port `5984` of the container
 * Runs everything as user `couchdb` (security ftw!)
 * Docker volume for data

## Planned Features

 * Explore Alpine Linux as base image.
 * Enable SSL automatically with a self-signed cert if none provided

## Usage

This project is still in development. It is not easily modifiable for "new" blogs, but stay tuned. I plan to make a self-installing version once the main features are complete. Essentially, this is a database for the [Rant](https://github.com/RamblingWare/Rant) backend. 

### Docker Deploy

> Coming soon...


### Build your own

Provide your own version of the `local.ini` for your custom CouchDB config.

Example Dockerfile:

```
FROM rant/database:latest

COPY local.ini /usr/local/etc/couchdb/local.d/
```

and then build and run

```
[sudo] docker build -t you/awesome-couchdb .
[sudo] docker run -d -p 5984:5984 -v ~/couchdb:/usr/local/var/lib/couchdb you/awesome-couchdb
```

## License

[Apache 2.0](/LICENSE)
