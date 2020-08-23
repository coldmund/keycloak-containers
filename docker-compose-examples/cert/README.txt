# make private key
openssl genrsa -des3 -out server.key 2048
# make request
openssl req -new -key server.key -out server.csr
# remove password(optional)
cp server.key server.key.origin
openssl rsa -in server.key.origin -out server.key
# make cert
openssl x509 -req -days 3650 -in server.csr -signkey server.key -out server.crt

