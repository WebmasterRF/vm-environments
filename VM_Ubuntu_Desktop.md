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

## 1. Install Ubuntu VB

#### 1. Download Ubuntu
[Download Ubuntu](https://www.ubuntu.com/download/desktop)

#### 2. Create VM (New)

Name: [Name of machine]
Type: Linux
Version: Ubuntu (64bit)
Memory size: 3000 MB
Hard disk: Create a virtual hard disk now
Hard disk file type: VDI
Storage on physical hard disk: Fixed size: 30 GB

#### 3. Install Ubuntu

### 1
Start new VB
Select start-up disk: search folder for Ubuntu ISO file
Start install

### 2
Install Ubuntu
English Keyboard
Updates and other software: normal installation, other options: check all
Installation type: Erase disk and install Ubuntu
Install Now
Continue
Where are you? your location
Username: rbn
password: rbn123
login automatically
Sit back and wait
Restart

### 3
Remove disk: 
Devices -> Optical Drives -> Select ISO
Devices -> Optional Drives -> Remove disk from virtual drive
Force Unmount
Enter

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

---

## 6. MongoDB

Download mongodb: https://www.mongodb.com/download-center/community

Version: latest version
OS: Ubuntu 18.04 Linux 64-bit x64
Package: server

Extract -> Home folder

Create DB folder: Home/mongodb-data

Initialize/Start DB
`rft@rft:~$ /home/rft/mongodb/bin/mongod --dbpath=/home/rft/mongodb-data`


db.createUser({
    user: "admin",
    pwd: "password",
    roles: [ { role: "dbOwner", db: "rftracking" } ]
})

MongoDB Tuts: https://studio3t.com/knowledge-base/categories/mongodb-tutorials/

## Robo 3T

Download Robo 3T: https://robomongo.org/download

Click download -> choose OS

Extract -> Home folder

Rename file to robo3t

Open Robo 3T: Home/robo3t/bin/robo3t

Create new connection


