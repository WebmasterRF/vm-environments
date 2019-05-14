# VM Environment Setup

_Average time to complete setup: 2 hrs._

Requirements:
  * [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  * [Vagrant](https://www.vagrantup.com/downloads.html)
  * [Git](https://git-scm.com/downloads)

References:
  * [Install Nginx on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-16-04)
  * [Node.js Application for Production on Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-node-js-application-for-production-on-ubuntu-16-04)
  * [NodeSource Node.js Binary Distributions](https://github.com/nodesource/distributions)

---

## 1. Install Ubuntu

#### 1. Create new project folder
Use Windows File Explore to create a new project folder. Then 'right-click' folder, select 'GIT Bash Here'

#### 2. Add Ubuntu/Xenial64 VagrantBox
`> vagrant box add ubuntu/xenial64`

#### 3. Initialize
`> vagrant init ubuntu/xenial64`

`> vagrant up`

#### 4. Vagrant-VBGuest plugin

`> vagrant halt`

`> vagrant plugin install vagrant-vbguest`

`> vagrant reload`

---

## 2. Install Nginx

#### 1. SSH into VM
`> vagrant ssh`

#### 2. Install Nginx
`> sudo apt-get update && sudo apt-get upgrade`

`> sudo apt-get -y install nginx`

`> sudo service nginx start`

---

## 3. Install NodeJS

#### 1. SSH into VM
`> vagrant ssh`

#### 2. Install NodeJS
`> sudo apt-get update && sudo apt-get upgrade`

Install NVM - https://github.com/creationix/nvm
`> curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash`

`> exit`

`> vagrant ssh`

`> nvm install node`

---

## 3. Install PM2

#### 1. SSH into VM
`> vagrant ssh`

#### 2. Install PM2
`> sudo npm install -g pm2`

`> pm2 start [application name]`

`> pm2 startup systemd`

`> sudo env PATH=$PATH:/usr/bin /usr/lib/node_modules/pm2/bin/pm2 startup systemd -u vagrant --hp /home/vagrant`

sudo env PATH=$PATH:/home/vagrant/.nvm/versions/node/v11.13.0/bin /usr/local/lib/node_modules/pm2/bin/pm2 startup systemd -u vagrant --hp /home/vagrant

`> systemctl status pm2-vagrant`

---

## 4. Set Up Nginx as a Reverse Proxy Server

`> sudo nano /etc/nginx/sites-available/default`

---

## 5. PostgresQL

https://leithsuheimat.wordpress.com/2017/12/18/installing-postgresql-10-on-ubuntu-16-04-on-virtualbox/
https://tecadmin.net/install-postgresql-server-on-ubuntu/

`> sudo apt-get update && sudo apt-get upgrade`

`> sudo add-apt-repository 'deb http://apt.postgresql.org/pub/repos/apt/ bionic-pgdg main'`

`> wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -`

`> sudo apt-get update`

`> sudo apt-get install postgresql postgresql-contrib`

Change password:

`> sudo -u postgres psql`

`> \password postgres`