# Linux

## Generate self signed certificate for _https:_//my-host.name
```
# Variables
export CERT_PUBLIC_KEY="MyPublicKey.crt"
export CERT_PRIVATE_KEY="MyPrivateKey.key"
export CERT_EXPIRY_DAYS=3650
export CERT_HOST="my-host.name"
# Command
openssl req -x509 -out $CERT_PUBLIC_KEY -keyout $CERT_PRIVATE_KEY -newkey rsa:2048 -nodes -sha256 -days $CERT_EXPIRY_DAYS -subj '/CN=$CERT_HOST' -extensions EXT -config <( printf "[dn]\nCN=$CERT_HOST\n[req]\ndistinguished_name = dn\n[EXT]\nsubjectAltName=DNS:$CERT_HOST\nkeyUsage=digitalSignature\nextendedKeyUsage=serverAuth")
```