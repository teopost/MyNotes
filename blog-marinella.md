Installazione blog Mary
===

Memo nel caso dovessi reinstallare tutto da capo


1. Creato vm debian su cloudatcost
2. Installato wordpress (http://www.edmondweblog.com/index.php/2015/03/23/installare-wordpress-4-1-1-su-debian-jessie)
3. Modificato ```/etc/apache2/sites-enabled/000-default.conf``` e messo DocumentRoot ```/var/www/html/wordpress```
4. Modificato vi /etc/apache2/apache2.conf  e aggiunto ```ServerName www.marinellamazzoli.it``` per togliere warning restart di apache
