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

## Creating a Linux service with systemd
```
# create yourServiceName.service file in /etc/systemd/system (may require sudo)
nano /etc/systemd/system/yourServiceName.service

# write the contents of your file yourServiceName.service
[Unit]
Description=<description about this service>

[Service]
Type=simple
User=<user e.g. root>
WorkingDirectory=<directory_of_script e.g. /root>
ExecStart=<script which needs to be executed>
EnvironmentFile=<location of enivronment file, eg. yourService.env, to set the environment variables for your service, e.g. JAVA_HOME=/location/of/jdk>
Restart=always

[Install]
WantedBy=multi-user.target

# reload the service files to include the new service.
sudo systemctl daemon-reload

# start your service
sudo systemctl start yourServiceName.service

# check the status of your service
sudo systemctl status yourServiceName.service

# enable your service on every reboot
sudo systemctl enable yourServiceName.service

# disable your service on every reboot
sudo systemctl disable yourServiceName.service
```
Ref:
[sshalert repo](https://github.com/groovemonkey/sshalert/blob/master/sshalert.service), 
[blog-post-1](https://www.shubhamdipt.com/blog/how-to-create-a-systemd-service-in-linux/), 
[blog-post-2](https://medium.com/@benmorel/creating-a-linux-service-with-systemd-611b5c8b91d6), 
[systemd-unit](https://www.freedesktop.org/software/systemd/man/systemd.unit.html), 
[systemd-service](https://www.freedesktop.org/software/systemd/man/systemd.service.html)
[config-details](https://linuxconfig.org/how-to-create-systemd-service-unit-in-linux)
