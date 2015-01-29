# Install soft

### MongoDB

Import the public key used by the package management system.

    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10

Create a /etc/apt/sources.list.d/mongodb.list file for MongoDB.

    echo 'deb http://downloads-distro.mongodb.org/repo/debian-sysvinit dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list

Reload local package database.

    sudo apt-get update

Install the MongoDB packages.

    sudo apt-get install -y mongodb-org

### Nvm & Node.js & Npm

Install script

    wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.23.2/install.sh | bash

To activate nvm, you need to source it from your shell (when needed)

    source ~/.nvm/nvm.sh

Install stable

    nvm install stable

### Forever.js

Install

    npm i forever -g

### Git

Install

    sudo apt-get install git -y

Gen pub_rsa

    ssh-keygen

### Nginx

Install

    sudo apt-get install nginx -y

Start

    sudo service nginx start

Edit conf

    sudo nano /etc/nginx/nginx.conf
    
    user www-data;
    worker_processes 4;
    pid /var/run/nginx.pid;

    events {
	    worker_connections 768;
	    # multi_accept on;
    }

    http {
    ##
	# Basic Settings
	##

	sendfile on;
	tcp_nopush on;
	tcp_nodelay on;
	keepalive_timeout 65;
	types_hash_max_size 2048;
	# server_tokens off;

	# server_names_hash_bucket_size 64;
	# server_name_in_redirect off;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;

	##
	# Logging Settings
	##

	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	##
	# Gzip Settings
	##

	gzip on;
	gzip_disable "msie6";

    server {
    
    # IP, который мы будем слушать
    listen 80;

    location / {
        # IP и порт, на которых висит node.js
        proxy_pass http://localhost:3080;
        proxy_set_header Host $host;
    }
    }
    }


Restart
    sudo service nginx restart
