Installazione wordpress
===

Sito WEDO
---

1. https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04
2. https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04
3. https://www.digitalocean.com/community/tutorials/how-to-configure-secure-updates-and-installations-in-wordpress-on-ubuntu
4. https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04

e alla fine

````
sudo chmod -R 777 /var/www/html/wp-content/uploads
````

In new version of apache2 you just following command like this:

```bash
sudo vi /etc/apache2/apache2.conf
```

Add the following new line end of file:

```
ServerName localhost
````

Then restart apache2:

```bash
sudo nano service apache restart
````

Attivare mod_rewrite

```bash
root@raspb3-wp:/etc/apache2/mods-available# a2enmod rewrite
Enabling module rewrite.
To activate the new configuration, you need to run:
service apache2 restart
root@raspb3-wp:/etc/apache2/mods-available# service apache2 restart
````

Configurare 

```
/etc/apache2/sites-available# vi 000-default.conf 

	DocumentRoot /var/www/html/wordpress
	ServerAdmin webmaster@localhost # dopo questo....
	
        RewriteEngine On

        <Directory /var/www/html/wordpress>
           Options FollowSymLinks
           AllowOverride All
        </Directory>
        
```

It's done.


