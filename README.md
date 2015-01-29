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
