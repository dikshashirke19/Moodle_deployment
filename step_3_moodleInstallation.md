# **Install Moodle on Ubuntu 20.04**
- Moodle is not a package that we can install using the APT package manager, instead, we have to download it manually.
```
$ cd ~/Downloads
```
Download
```
$ wget https://download.moodle.org/download.php/stable400/moodle-4.0.4.tgz
```

Extract the downloaded file:
```
$ tar -zxvf moodle-*tgz
```

# **Create an Nginx server block for Moodle**
```
$ sudo nano /etc/nginx/sites-available/moodle.conf
```


# Create an Nginx server block for Moodle
```
$ sudo nano /etc/nginx/sites-available/moodle.conf
```

Paste the following lines:
Note: Replace yourdomain.com with the domain you want to use to access Moodle. Also, don’t forget to change the PHP version in the below lines if you are using other than php8.0.

```
server {
listen 80;
listen [::]:80;
root /var/www/html/moodle;
index index.php index.html index.htm;
server_name yourdomain.com www.yourdomain.com;
location / {
try_files $uri $uri/ =404;
}
location ~ [^/]\.php(/|$) {
  include snippets/fastcgi-php.conf;
  fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
  fastcgi_param SCRIPT_FILENAME   $document_root$fastcgi_script_name;
  include fastcgi_params;
}
}

```
- Enable the Created Moodle server configuration block for Nginx:
```
$ sudo ln -s /etc/nginx/sites-available/moodle.conf /etc/nginx/sites-enabled/
```
### Check the Configuration for errors:
```
$ sudo nginx -t
```
Restart the Nginx server:
```
$ sudo systemctl restart nginx
```
Setting up Moodle on Ubuntu 20.04
For example – http://your-domain.com or http://your-ip.com


