Installazione VirtualBox server
===



VirtualBox is a cross-platform virtualization software package for x86 architecture. A nice thing about VirtualBox is that it has several quite useful features, not available on other similar software such as VMware Player, which include: virtual machine snapshots. disk image conversion and support (e.g., VMware's VMDK, Microsoft's VHD, Apple's DMG), guest machine cloning, etc.


Install VirtualBox on Ubuntu or Debian
---

First, update /etc/apt/sources.list to add the official repository of VirtualBox. Use the following command for that. The command will determine the release version of your Ubuntu or Debian, and update /etc/apt/sources.list file accordingly.

```bash
$ sudo sh -c "echo 'deb http://download.virtualbox.org/virtualbox/debian '$(lsb_release -cs)' contrib non-free' >> /etc/apt/sources.list"
```
Next, run the following commands to install VirtualBox.

```bash
$ wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install virtualbox-4.3
```

Configure VirtualBox Server
---
On the headless server side, you need to install VirtualBox 4.2.0 and higher.

Besides VirtualBox, you also need to install VirtualBox extension pack on the server. The extension pack is needed for remote desktop display and PXE booting.

Assuming that the version of the installed VirtualBox is 4.2.16, you can install the corresponding VirtualBox extension pack on the server as follows.

```bash
$ wget http://download.virtualbox.org/virtualbox/4.2.16/Oracle_VM_VirtualBox_Extension_Pack-4.2.16-86992.vbox-extpack
$ sudo VBoxManage extpack install ./Oracle_VM_VirtualBox_Extension_Pack-4.2.12-84980.vbox-extpack
```

To configure VirtualBox web service on the server, proceed as follows.

First, create a configuration file for the web service at /etc/default/virtualbox.

```bash
$ sudo vi /etc/default/virtualbox
```

Paste this configuration

```
VBOXWEB_USER="vbox"
VBOXWEB_TIMEOUT=0
VBOXWEB_LOGFILE="/var/log/vboxwebservice.log"
VBOXWEB_HOST=localhost
```
Note: localhost is valid only if service run on same server of virtualbox

In the configuration file, VBOXWEB_USER is set to the Linux user that you will run VirtualBox web service as, and VBOXWEB_HOST corresponds to the IP address of the server.

Next, initialize and set the ownership of the log file:

```bash
$ sudo touch /var/log/vboxwebservice.log
$ sudo chown vbox:vboxusers /var/log/vboxwebservice.log
```

Create VirtualBox configuration directory:

```bash
$ useradd -m vbox -G vboxusers
$ sudo mkdir /home/vbox/.VirtualBox
$ sudo chown vbox:vboxusers /home/vbox/.VirtualBox
```

Setting vbox password

```bash
$ passwd vbox
```

Start VirtualBox web service:

```bash
$ sudo service vboxweb-service start
```

Check the status of VirtualBox web service:

```bash
$ sudo service vboxweb-service status
```

```
Checking for VBox Web Service ...running
```

Also, verify that VirtualBox web service is listening on port 18083.

```bash
$ sudo netstat -nap | grep vboxwebsrv
```

tcp        0      0 127.0.0.1:18083        0.0.0.0:*               LISTEN      15855/vboxwebsrv
unix  3      [ ]         STREAM     CONNECTED     152848   15855/vboxwebsrv
This completes VirtualBox server configuration. Next, proceed to install RemoteBox on a client host.

Requirements for Installing RemoteBox on Client Host
---
Visit http://xmodulo.com/2013/07/how-to-manage-virtualbox-vms-on-remote-headless-server.html


Install phpVirtualbox
---
Download PHPVirtualBox

Now we can download PHPVirtualBox. Move to /var/www and download the latest version of the file:

```bash
$ wget http://phpvirtualbox.googlecode.com/files/ phpvirtualbox-4.1-10.zip
```
Note: Check the website for the latest version

Once downloaded, unzip the software and move it:

```bash
$ unzip phpvirtualbox-4.1-10.zip
$ mv phpvirtualbox-4.1-10 phpvirtualbox
```

Move to this new directory and then create the config.php file from the example:

```bash
$ cp config.php-example config.php
```

Configure PHPVirtualBox
---
Open up config.php in a text editor and add the details you need for the web server:

```php
/* Username / Password for system user that runs VirtualBox */
var $username = ‘vbox’;
var $password = ‘password’;
```

Now change apache default root 

Afterwards, restart the server and you should be ready to go.

Use username admin and password admin


Reference
---
* http://xmodulo.com/2013/03/how-to-install-or-upgrade-virtualbox-on-ubuntu-or-debian.html
* http://xmodulo.com/2013/07/how-to-manage-virtualbox-vms-on-remote-headless-server.html
* http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/
* http://remotebox.knobgoblin.org.uk/downloads.cgi
* http://www.linuxuser.co.uk/tutorials/build-a-headless-virtualisation-server/2
* http://wiki.ubuntu-it.org/Virtualizzazione/VirtualBox/AccessoRemoto



