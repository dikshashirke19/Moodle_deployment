# **Create Moodle Database (MariaDB)**
We can install MySQL, however, here we are using MariaDB (fork) which
is one of the best open-source database servers. It is available to install
using the default system repository of Ubuntu 20.04. Hence, just run the
given command:

```
$sudo apt install software-properties-common -y

$curl -LsS -O https://downloads.mariadb.com/MariaDB/mariadb_repo_setup

$sudo bash mariadb_repo_setup -mariadb-server-version=10.6

$sudo apt install mariadb-server

$sudo apt update

$sudo apt install mariadb-server
```
### Secure your Database server by setting up the root DB user password and removing anonymous rights.
```
$sudo mysql_secure_installation
```

### Create a Database and user for Moodle
- Once the installation is completed, let’s create a dedicated database for Moodle to use and save the data.
- Login to DB server CLI:
 - #Use the password you have set for it in the previous step.

## **Login to DB server CLI:**
- #Use the password you have set for it in the previous step.
```
$sudo mysql -u root -p
```
- Create Database:
```
Sql > CREATE DATABASE dbname;
```
- #Replace dbname name with whatever you want to use:
```
Sql > CREATE USER 'db_user'@'localhost' IDENTIFIED BY
'db_password';
```
- #Repalce db_user and db_password that you want to use.
```
Sql > GRANT ALL ON dbname.* TO 'db_user'@'localhost' IDENTIFIED BY 'db_password' WITH GRANT OPTION;
```
```
Sql > FLUSH PRIVILEGES;

Sql > EXIT;
```


