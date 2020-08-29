# install_GLPI
Create repo for instalation GLPI 9.4 on Ubuntu 18.04

# Install mariadb server
> sudo apt update

> sudo apt -y upgrade

> sudo apt install mariadb-server

> sudo mysql_secure_installation

# Config Maria DB
> sudo mysql -u root -p

> UPDATE mysql.user SET plugin = 'mysql_native_password' WHERE User = 'root';

> FLUSH PRIVILEGES;

> QUIT;

# Create a database and user for GLPI.
> mysql -u root -p

> CREATE DATABASE glpi;

> CREATE USER 'glpi'@'localhost' IDENTIFIED BY 'StrongDBPassword';

> GRANT ALL PRIVILEGES ON glpi.* TO 'glpi'@'localhost';

> FLUSH PRIVILEGES;

> EXIT;

# Install PHP and Apache
> sudo apt-get -y install php php-{curl,gd,imagick,intl,apcu,recode,memcache,imap,mysql,cas,ldap,tidy,pear,xmlrpc,pspell,gettext,mbstring,json,iconv,xml,gd,xsl}

> sudo apt-get -y install apache2 libapache2-mod-php

# Download and Install GLPI on Ubuntu 20.04/18.04
> sudo apt-get -y install wget

> export VER="9.4.5"

> wget https://github.com/glpi-project/glpi/releases/download/$VER/glpi-$VER.tgz

> tar xvf glpi-$VER.tgz

> sudo mv glpi /var/www/html/

> sudo chmod -R 755 /var/www/html/glpi/

> sudo chown -R www-data:www-data /var/www/html/

# Config file access GLPI
> sudo vim /etc/apache2/conf-available/glpi.conf

> add content:

 # <Directory "/var/www/html/glpi">    
   #   AllowOverride All 
 # "<"/Directory>
  
> sudo a2enconf glpi.conf

> sudo service apache2 restart




