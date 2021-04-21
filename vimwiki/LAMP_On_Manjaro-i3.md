## Install LAMP on Manjaro-i3

### L for linux

```
cat /proc/version
Linux version 5.10.19-1-MANJARO (builduser@LEGION) (gcc (GCC) 10.2.0, GNU ld (GNU Binutils) 2.36.1) #1 SMP PREEMPT Fri Feb 26 11:38:34 UTC 2021
```

#### Preparation

- Update system

```

sudo pacman -Syyu

```

- If errors occurred when you try to install mysql:
```
error: failed to commit transaction (conflicting files)
mysql: /usr/bin/mysql_upgrade exists in filesystem (owned by mariadb-clients)
mysql: /usr/bin/mysqlbinlog exists in filesystem (owned by mariadb-clients)
mysql: /usr/bin/mysqltest exists in filesystem (owned by mariadb-clients)
mysql: /usr/share/man/man1/mysql_upgrade.1.gz exists in filesystem (owned by mariadb-clients)
mysql: /usr/share/man/man1/mysqlbinlog.1.gz exists in filesystem (owned by mariadb-clients)
Errors occurred, no packages were upgraded.
```

try command below then install mysql again:

```
sudo pacman -R mariadb mariadb-clients mariadb-lib*
```



### A for Apache

#### Install apache

```
sudo pacman -S apache
```

#### Start apache

- enable apache start on boot

```
sudo systemctl enable httpd.service
```

- reboot apache

```
sudo systemctl restart httpd.service
```

- verify whether apache is running 

```
sudo systemctl status httpd.service

● httpd.service - Apache Web Server
     Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; vendor preset: disabled)
     Active: active (running) since Mon 2021-03-15 23:09:22 CST; 14min ago
   Main PID: 243579 (httpd)
      Tasks: 7 (limit: 9431)
     Memory: 8.9M
     CGroup: /system.slice/httpd.service
             ├─243579 /usr/bin/httpd -k start -DFOREGROUND
             ├─243582 /usr/bin/httpd -k start -DFOREGROUND
             ├─243583 /usr/bin/httpd -k start -DFOREGROUND
             ├─243584 /usr/bin/httpd -k start -DFOREGROUND
             ├─243585 /usr/bin/httpd -k start -DFOREGROUND
             ├─243586 /usr/bin/httpd -k start -DFOREGROUND
             └─243589 /usr/bin/httpd -k start -DFOREGROUND

3月 15 23:09:22 kamisama-20e0a013cd systemd[1]: Started Apache Web Server.

```

- test apache

- The default apache root directory is `/srv/http/`,create a index page :

`sudo vim /srv/http/index.html`

- Then add the following:

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta http-equiv="X-UA-Compatible" content="ie=edge" />
  <title>Welcome</title>
 </head>
<body>
  <h2>Welcome to my Web Server test page</h2>
</body>
</html>
```

- Open the browser and navigate to :
  - http://localhost for your own machine(local environment) 
    OR
  - `http://IP-address` for your server machine  
    Then you will see the test page.


#### Configure apache

##### make it support php(configure apache PHP module)

> PHP and php-apache need to be installed before you start. See [Install PHP](#Install_PHP)

open and edit this file:`/etc/httpd/conf/httpd.conf`

1. comment out the following line in , if it is not already:
```
[...]
#LoadModule unique_id_module modules/mod_unique_id.so
[...]
```
    
2. find and comment out the following line:   
```
[...]
#LoadModule mpm_event_module modules/mod_mpm_event.so
[...]
```
    
3. uncomment or add the line:     
  ```
  LoadModule mpm_prefork_module modules/mod_mpm_prefork.so
  ```

4. then add the following lines at the bottom:
  
php8:   

  ```
  LoadModule php_module modules/libphp.so
  AddHandler php-script php
  Include conf/extra/php_module.conf
  ```      

php7:

  ```
  LoadModule php7_module modules/libphp7.so
  AddHandler php7-script php
  Include conf/extra/php7_module.conf
  
  ```
  
5. save and close the file.then restart appache:   
```
sudo systemctl restart httpd.service
```

<a name="Test_PHP"></a>

6. test PHP:  
   create a test file `index.php` in apache root directory:
   `touch /srv/http/index.php`   
   add the following lines:   
   ```
   <?php
   phpinfo();
   ?php>
   ```
   open browser and navigate to http://localhost/index.php


### M for Mysql

#### Install Mysql
   
>  MariaDB is now officially the default implementation of MySQL in Arch Linux since 2013.
   
   ```
   sudo pacman -S mysql
   resolving dependencies...
looking for conflicting packages...

Packages (1) mysql-8.0.23-1

Total Installed Size:  163.90 MiB

:: Proceed with installation? [Y/n] y
(1/1) checking keys in keyring                                                             [#####################################################] 100%
(1/1) checking package integrity                                                           [#####################################################] 100%
(1/1) loading package files                                                                [#####################################################] 100%
(1/1) checking for file conflicts                                                          [#####################################################] 100%
(1/1) checking available disk space                                                        [#####################################################] 100%
:: Processing package changes...
(1/1) installing mysql                                                                     [#####################################################] 100%
:: You need to initialize the MySQL data directory prior to starting
   the service. This can be done with mysqld --initialize command, e.g.:
   mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql
:: Additionally you should secure your MySQL installation using
   mysql_secure_installation command after starting the mysqld service
Optional dependencies for mysql
    perl-dbd-mysql: for mysqlhotcopy, mysql_convert_table_format and mysql_setpermission
:: Running post-transaction hooks...
(1/3) Reloading system manager configuration...
(2/3) Creating temporary files...
(3/3) Arming ConditionNeedsUpdate...

   ```
   
   Look the installation info:
   ```
:: You need to initialize the MySQL data directory prior to starting
   the service. This can be done with mysqld --initialize command, e.g.:
   mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql
:: Additionally you should secure your MySQL installation using
   mysql_secure_installation command after starting the mysqld service

   ```
   
   - Initialize Mysql data directory:
      
      ```
      mysqld --initialize --user=mysql --basedir=/usr --datadir=/var/lib/mysql
      ```   
      
#### Start Mysql

- enable start on boot

```
sudo systemctl enable mysqld.service
```

- start mysql server

```
sudo systemctl start mysqld.service
```

- verify whether mysql is running or not

```
sudo systemctl status mysqld.service
● mysqld.service - MySQL Server
     Loaded: loaded (/usr/lib/systemd/system/mysqld.service; enabled; vendor preset: disabled)
     Active: active (running) since Tue 2021-03-16 10:37:14 CST; 5s ago
       Docs: man:mysqld(8)
             http://dev.mysql.com/doc/refman/en/using-systemd.html
    Process: 267797 ExecStartPre=/usr/bin/mysqld_pre_systemd (code=exited, status=0/SUCCESS)
   Main PID: 267818 (mysqld)
     Status: "Server is operational"
      Tasks: 38 (limit: 9431)
     Memory: 352.4M
     CGroup: /system.slice/mysqld.service
             └─267818 /usr/bin/mysqld

3月 16 10:37:13 kamisama-20e0a013cd systemd[1]: Starting MySQL Server...
3月 16 10:37:13 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:13.684260Z 0 [Warning] [MY-010915] [Server] 'NO_ZERO_DATE', 'NO_ZERO_IN_DATE' and>
3月 16 10:37:13 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:13.684331Z 0 [System] [MY-010116] [Server] /usr/bin/mysqld (mysqld 8.0.23) starti>
3月 16 10:37:13 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:13.697374Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
3月 16 10:37:13 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:13.896893Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
3月 16 10:37:14 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:14.013163Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-a>
3月 16 10:37:14 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:14.069166Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
3月 16 10:37:14 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:14.069404Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to suppo>
3月 16 10:37:14 kamisama-20e0a013cd mysqld[267818]: 2021-03-16T02:37:14.090666Z 0 [System] [MY-010931] [Server] /usr/bin/mysqld: ready for connections>
3月 16 10:37:14 kamisama-20e0a013cd systemd[1]: Started MySQL Server.

```

- setup mysql root user password

```
sudo mysql_secure_installation
```

sampel output:
```
NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
SERVERS IN PRODUCTION USE! PLEASE READ EACH STEP CAREFULLY!
In order to log into MariaDB to secure it, we'll need the current
password for the root user. If you've just installed MariaDB, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.
Enter current password for root (enter for none): `## Press Enter`
OK, successfully used password, moving on...
Setting the root password ensures that nobody can log into the MariaDB
root user without the proper authorisation.
Set root password? [Y/n] `## Press Enter`
New password: `## Enter password`
Re-enter new password: `## Re-enter password`
Password updated successfully!
Reloading privilege tables..
... Success!

By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them. This is intended only for testing, and to make the installation
go a bit smoother. You should remove them before moving into a
production environment.
Remove anonymous users? [Y/n] `## Press Enter`
... Success!

Normally, root should only be allowed to connect from 'localhost'. This
ensures that someone cannot guess at the root password from the network.
Disallow root login remotely? [Y/n] `## Press Enter`
... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access. This is also intended only for testing, and should be removed
before moving into a production environment.
Remove test database and access to it? [Y/n] `## Press Enter`
- Dropping test database...
... Success!
- Removing privileges on test database...
... Success!
Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.
Reload privilege tables now? [Y/n] `## Press Enter`
... Success!
Cleaning up...
All done! If you've completed all of the above steps, your MariaDB
installation should now be secure.
Thanks for using MariaDB!

MariaDB has been installed and ready to use.


```
since MariaDB is derived from MYSQL, the procedure above should fit both.

### P for PHP(or python)

<a name="Install_PHP"></a>
#### Install PHP 

```
sudo pacman -S php
```

install apache php module

```
sudo pacman -S php-apache
```

#### Test PHP

See [Test PHP](#Test_PHP)

#### Install phpMyAdmin

phpMyAdmin is a graphical MySQL/MariaDB administration tool that can be used to create, edit and delete databases.

install phpmyadmin:

`sudo pacman -S phpmyadmin`

edit `php.ini`

`sudo vim /etc/php/php.ini`
 
uncomment the following lines:

```
[...]
extension=bz2
extension=mysqli
extension=iconv
[...]
```

save and close the file.

Next, create a configuration file for phpMyAdmin.

`sudo vim /etc/httpd/conf/extra/phpmyadmin.conf`

add the following lines:

```
Alias /phpmyadmin "/usr/share/webapps/phpMyAdmin"
<Directory "/usr/share/webapps/phpMyAdmin">
DirectoryIndex index.php
AllowOverride All
Options FollowSymlinks
Require all granted
</Directory>
```

then, open Apache configuration file:

`sudo vim /etc/httpd/conf/httpd.conf`

add the following line at the end

`Include conf/extra/phpmyadmin.conf`

save and close the file.

Restart `httpd`(apache) service again.

`sudo systemctl restart httpd`


##### Test phpmyadmin 

Open your browser and navigate to http://localhost/phpmyadmin .

You might see an error that says “The configuration file now needs a secret passphrase
(blowfish_secret)” at the bottom of phpMyAdmin dashboard.

To get rid of this error, edit `/etc/webapps/phpmyadmin/config.inc.php` file,

``` 
$cfg['blowfish_secret'] = '`MyP@$S`'; /* YOU MUST FILL IN THIS FOR COOKIE AUTH!$ /**
```
Save and close the file. Restart Apache service.

`sudo systemctl restart httpd.service`
