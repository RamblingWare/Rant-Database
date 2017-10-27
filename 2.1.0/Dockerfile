FROM apache/couchdb:2.1.0

LABEL maintainer="Austin Delamar @amdelamar" \
      description="Blog system on CouchDB."

# SSL certificate
RUN mkdir /opt/couchdb/cert \
  && cd /opt/couchdb/cert \
  && openssl genrsa -out privkey.pem 4096 -noout \
  && openssl req -new -x509 -days 1826 -key privkey.pem -out cert.pem -subj "/C=US/ST=-/L=-/O=Test/OU=Test/CN=IT/emailAddress=info@example.com" \
  && chmod +x privkey.pem cert.pem \
  && chown couchdb privkey.pem cert.pem
  
# Add configuration
COPY local.ini /opt/couchdb/etc/local.d/
COPY vm.args /opt/couchdb/etc/

EXPOSE 6984
