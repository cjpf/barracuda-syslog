# barracuda-syslog
A dockerized implementation of the barracuda-syslog-api and barracuda-syslog-interface projects.  This also configures syslog-ng, mysql and postfix containers to support those applications.
This application has not been deployed as an AMI or on any services like Kubernetes at this time. 

# Deployment
## System Setup
If you are using your own system with shell access, I recommend using Ubuntu 19.10 for deployment of this application.  This application will not work without a valid SSL certificate.  You may provide one of your own that matches the hostname for the application, or you may generate your own using the instructions below.


## Generating a Standalone Certificate with Let's Encrypt certbot
Install certbot;
> sudo apt-get update
> sudo apt-get install software-properties-common
> sudo add-apt-repository universe
> sudo add-apt-repository ppa:certbot/certbot
> sudo apt-get update
> sudo apt-get install certbot

Generate certificates;
> sudo certbot certonly --standalone


Once the certificates have been generated, copy them into the proper directory for Docker to use them in the syslog-ng and nginx containers. 

> cp /etc/letsencrypt/live/<hostname+fqdn>/chain.pem barracuda-syslog/services/certificates/ca.d/ca.pem
> cp /etc/letsencrypt/live/<hostname+fqdn>/fullchain.pem barracuda-syslog/services/certificates/cert.d/cert.pem
> cp /etc/letsencrypt/live/<hostname+fqdn>/privkey.pem barracuda-syslog/services/certificates/cert.d/key.pem

Navigate to the ca.d directory and generate a hash of the CA file.  We will create a link to this file using the generated hash.

> cd barracuda-syslog/services/certificates/ca.d
> ln -s barracuda-syslog/services/certificates/ca.d/ca.pem barracuda-syslog/services/certificates/ca.d/`openssl x509 -noout -hash -in ca.pem`.0
> openssl x509 -noout -hash -in ca.pem
