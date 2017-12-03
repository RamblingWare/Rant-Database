FROM apache/couchdb:2.1.1

LABEL maintainer="Austin Delamar @amdelamar" \
      description="Blog system on CouchDB."

# SSL certificate
RUN mkdir -p /opt/couchdb/etc/cert \
  && cd /opt/couchdb/etc/cert \
  && openssl genrsa -out privkey.pem 2048 -noout \
  && openssl req -new -x509 -days 1826 -key privkey.pem -out cert.pem -subj "/C=US/ST=-/L=-/O=Test/OU=Test/CN=IT/emailAddress=info@example.com" \
  && chmod 600 privkey.pem cert.pem \
  && chown couchdb privkey.pem cert.pem

# Add configuration
COPY local.ini /opt/couchdb/etc/local.d/
COPY vm.args /opt/couchdb/etc/

EXPOSE 5984 6984
