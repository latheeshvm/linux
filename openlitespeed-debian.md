# one click available : https://openlitespeed.org/kb/1-click-install/

sudo apt update
sudo apt upgrade

#track
934M /13G

sudo apt install wget

wget -O - http://rpms.litespeedtech.com/debian/enable_lst_debian_repo.sh | bash
sudo apt install openlitespeed
sudo apt update

apt-get install lsphp81 lsphp81-common lsphp81-curl lsphp81-mysql lsphp81-opcache lsphp81-imap
sudo apt update

#update the password
cd /usr/local/lsws/admin/misc
./admpass.sh 

systemctl start lsws

#access the port : :7080

cd /usr/local/lsws/
mkdir {website_folder} ##eg mkdir website
mkdir html ( inside /usr/local/lsws/website/ )
create an index file with phpinfo() # for testing

open the port 80

Vistual Hosts


website
/usr/local/lsws/website/
$SERVER_ROOT/conf/vhosts/$VH_NAME/vhconf.conf

Enable Scripts : YES
Restrained : YES

document root :/usr/local/lsws/website/html
domainname : use the ip

index files : 
index.php

create the listner on port 80, and set the virtual host mapping to website and domain as IP


Enter the External App Details: Fill in the details for the external application:

Name: lsphp81 (or any name you prefer).
Address: uds://tmp/lsphp81.sock (Unix Domain Socket path).
Max Connections: 35 (or the maximum number of PHP connections you want to allow).
Environment: Add the PHP_LSAPI_CHILDREN=35 line (or adjust the number as per your server requirements).
Initial Request Timeout (secs): 60.
Retry Timeout (secs): 0.
Command: /usr/local/lsws/lsphp81/bin/lsphp (the path to your lsphp81 binary).
Back Log: 100, Instances: 1, Memory Soft Limit (bytes): 2047M, Memory Hard Limit (bytes): 2047M, and Process Soft Limit: 400.


Enter the Script Handler Details: Fill in the details for the script handler:

Suffixes: php.
Handler Type: LiteSpeed SAPI.
Handler Name: lsphp81 (or whatever name you used in step 4).


sudo apt-get install mariadb-server

sudo mysql -u root -p

CREATE DATABASE wordpress_db;
CREATE USER 'wordpress_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON wordpress_db.* TO 'wordpress_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;

chown -R nobody:nogroup /usr/local/lsws/Example/html/

