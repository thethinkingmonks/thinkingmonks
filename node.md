# 1. Installation

## Install nodejs and npm
```shell
sudo apt install -y build-essential nodejs npm 
```

## Install NVM
Go the github repo https://github.com/nvm-sh/nvm to install the latest version of nvm
```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
source ~/.bashrc
```
Note: Do not use sudo it will enable root access to nvm

## List all the version of node
```shell
nvm list-remote
```

## List of node version installed in nvm
```shell
nvm list
```

## Install particular version of node in nvm
```shell
nvm install lts/fermium
```

## Switch between installed version of node
```shell
nvm use v14.10.0
```

# 2. Project Creation
## Start new projects with npm init
```shell
npm init --yes
npm config set init.author.name ThinkingMonks
npm config set init.author.email thethinkingmonks@gmail.com
```

## View the process of node application using pm2
PM2 is a process manager for Node.js applications. PM2 makes it possible to daemonize applications so that they will run in the background as a service.

```shell
sudo npm install pm2@latest -g
```
