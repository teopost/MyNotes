Installazione wordpress
===

Blog Mary
---

Memo nel caso dovessi reinstallare tutto da capo


1. Creato vm debian su cloudatcost
2. Installato wordpress (http://www.edmondweblog.com/index.php/2015/03/23/installare-wordpress-4-1-1-su-debian-jessie)
3. Modificato ```/etc/apache2/sites-enabled/000-default.conf``` e messo DocumentRoot ```/var/www/html/wordpress```
4. Modificato vi /etc/apache2/apache2.conf  e aggiunto ```ServerName www.marinellamazzoli.it``` per togliere warning restart di apache
5. 

Sito WEDO
---

1. https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-14-04
2. https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04
3. https://www.digitalocean.com/community/tutorials/how-to-configure-secure-updates-and-installations-in-wordpress-on-ubuntu

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

It's done.


