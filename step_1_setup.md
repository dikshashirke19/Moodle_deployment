# **Update Ubuntu 20.04**
Start with updating the system to install the latest available updates and refresh the APT package index cache.
```
$sudo apt update
```

# **Install Nginx and PHP**
install the Nginx web server
```
$sudo apt install nginx
```
## Setup PHP 8.x on Ubuntu 20.04
The version of PHP available through the default repository of Ubuntu is 7.4, we are installing PHP 8.0, the latest version of the PHP, we need to add an extra repository.
```
$sudo apt install software-properties-common
$sudo add-apt-repository ppa:ondrej/php
```
## Install PHP 8.0 and extensions:
```
sudo apt install php8.0 php8.0-{fpm,common,mbstring,xmlrpc,soap,gd,xml,intl,mysql,cli,mcrypt,ldap,zip,curl}

```
To check the version:
```
$php -v
```
### **Now, edit the php.ini file to change some values.**
```
$sudo vim /etc/php/8.0/fpm/php.ini
```
- Note: If you are using the default version of PHP or any other then change 8.0 with that in the above command.
- Find the following lines and change their values
```
memory_limit = 256M
upload_max_filesize = 64M
max_execution_time = 360
```
- also don’t forget to remove the semicolon (;) given in front of
max_input_vars.
```
max_input_vars = 5000
```

- Change the time zone to your time zone
```
timedatectl set-timezone "Asia/Kolkata"
```

- restart the service
```
sudo service php8.0-fpm restart
```



