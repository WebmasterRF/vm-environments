# VM Environment Setup

_Average time to complete setup: 2 hrs._

Requirements:
  * [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
  * [Vagrant](https://www.vagrantup.com/downloads.html)
  * [Git](https://git-scm.com/downloads)
  * [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)

References:
  * [Install Ubuntu on new VM](https://www.taniarascia.com/what-are-vagrant-and-virtualbox-and-how-do-i-use-them/)
  * [Install Apache, PHP, and MySQL on new VM](https://www.taniarascia.com/how-to-install-apache-php-7-1-and-mysql-on-ubuntu-with-vagrant/)
  * [Setup PHP 7.2 mod_rewrite](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04)
  * [Vagrantbox Search](https://app.vagrantup.com/boxes/search)

---

## 2. Install Apache

#### 1. Install Apache
`> sudo apt-get update && sudo apt-get upgrade`

`> sudo apt-get install apache2 -y`

#### 2. Set servername
`> sudo nano /etc/apache2/apache2.conf`

At the bottom of the apache2.conf file, type:
```
ServerName localhost
```

#### 3. Test setup
`> sudo service apache2 restart`

`> sudo apache2ctl configtest`

`> apache2 -v`

---

## 3. Install PHP 7.3

#### 1. SSH into VM
`> vagrant ssh`

#### 2. Install php
`> sudo apt-add-repository ppa:ondrej/php`

`> sudo apt-get update`

`> sudo apt-get install php7.3`

#### 3. Test PHP
`> php -v`

#### 4. Install PHP extensions
`> sudo apt install php7.3-bcmath php7.3-bz2 php7.3-cgi php7.3-cli php7.3-common php7.3-curl php7.3-dev php7.3-enchant php7.3-fpm php7.3-gd php7.3-imap php7.3-intl php7.3-json php7.3-ldap php7.3-mbstring php7.3-odbc php7.3-opcache php7.3-pgsql php7.3-pspell php7.3-readline php7.3-sqlite3 php7.3-tidy php7.3-xml php7.3-xmlrpc php7.3-zip`

If you get this message, run the listed commands with sudo:
```
NOTICE: Not enabling PHP 7.3 FPM by default.
NOTICE: To enable PHP 7.3 FPM in Apache2 do:
NOTICE: a2enmod proxy_fcgi setenvif
NOTICE: a2enconf php7.3-fpm
NOTICE: You are seeing this message because you have apache2 package installed.
```

`> sudo service apache2 restart`

#### 5. SOAP (only if required)
`> sudo apt-get install php7.3-soap`

`> sudo service php7.3-fpm reload`

`> sudo service apache2 restart`

---

## 5. Setup ModRewrite

#### 1. Enabling mod_rewrite
`> sudo a2enmod rewrite`

`> sudo service apache2 restart`

#### 2. Setup .htaccess
`> sudo nano /etc/apache2/sites-available/000-default.conf`

Add this code to '000-default.conf' file, right after line: `<VirtualHost *:80>`
```
<Directory /var/www/html>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Require all granted
</Directory>
```

`> sudo service apache2 restart`

`> sudo chmod o+w /var/www/html`

`> sudo nano /var/www/html/.htaccess`

Add this code to .htaccess file:
```
RewriteEngine on
```

---

## 6. Install MySQL

#### 1a. Use Windows Comman Prompt
Open Windows Command Promt to install MySQL. Cmder terminal act weird when setting the password.

#### 1. SSH into VM
`> vagrant ssh`

#### 2. Install MySQL
`sudo apt-get install mysql-server php7.3-mysql`

When asked to set password: `root`

#### 3. Edit my.cnf
`sudo nano /etc/mysql/my.cnf`

Comment out:

`# skip-external-locking`

`# bind-address 0.0.0.0`

#### 4. Restart Apache and MySQL
`sudo service apache2 restart`

`sudo service mysql restart`

#### 5. Exit VM
`> exit`

---

## 7. Setup MySQL Workbench

#### 1. Create new connection
Hit the + icon to add a new connection

#### 2. Change connection method
Change dropbox to `Standard TCP/IP over SSH`

#### 3. Parameter settings

SSH Hostname: `192.168.33.10`

SSH Username: `vagrant`

SSH Key File: `c:\[project folder path]\.vagrant\machines\default\virtualbox\private_key`

MySQL Hostname: `127.0.0.1`

MySQL Server Port: `3306`

Username: `root`

#### 4. Start connection

SSH Password: `vagrant`

MySQL Password: `root`

---

## Composer

`> curl -Ss https://getcomposer.org/installer | php`

`> sudo mv composer.phar /usr/bin/composer`

---

## 8. Install NodeJS

#### Install NodeJS
`> sudo apt-get update && sudo apt-get upgrade`

Install NVM - https://github.com/creationix/nvm
`> curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash`

close / reopen terminal

`> nvm install node`

---

## 9. PostgresQL

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

## 6. PGAdmin

https://askubuntu.com/questions/831262/how-to-install-pgadmin-4-in-desktop-mode-on-ubuntu

To Run:

`> ~/pgadmin4/pgadmin4`