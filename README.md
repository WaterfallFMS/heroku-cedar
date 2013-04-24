# Intro

This is a vagrant Heroku cedar stack instance that can be used to manually test an application in a heroku like environment.  It uses the precompiled version of [heroku-cedar](https://github.com/ejholmes/vagrant-heroku).

# Simple Setup

1. Edit the Vagrantfile and add any configs that your app might need
  1. By default we port forward port 3000 on your local machine to port 3000 on the VM
1. Add any applications that you want to run to this folder
1. `vangrant up`
1. `vangrant ssh`
1. `cd /vagrant`
1. Run your app binding to port 3000
1. Open [http://localhost:3000](http://localhost:3000) in your browser

## Subdomains and XIP.io

Using `localhost` or IP addresses directly as a URL prevents the use of certain DNS features like subdomains.  If you need these features then you will need to use a services that an translate IPs in to DNS.  This is where [xip.io](http://xip.io).

Xip.io is a special DNS server which resolves to a provided IP, but maintains subdomains.  For example:

    127.0.0.1.xip.io -> resolves to 127.0.0.1 (localhost)
    secure.127.0.0.1.xip.io -> resolves to the secure subdomain of localhost
    
## Foreman

Foreman is used by Heroku to run workers and websites in one shot from a Procfile.  However, foreman does not manage manage the environment like Heroku does so you will still need to do this manually.

### Bash

    echo "export SOME_VAR=value" >> env
    source env & foreman start
