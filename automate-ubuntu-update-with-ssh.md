Automate ubuntu software update
===
Quick and simple system to automate updates throughout all of my systems.
Note: sudo will be installed

1. Create apt-automate
--- 
Create a shell script named apt-automate into /usr/local/bin folder. You shoud be root.

    # vi /usr/local/bin/apt-automate

Now paste this code

``` bash
#!/bin/sh
apt-get update && apt-get -u -y upgrade
```

2. Setting sudo permission
---
Edit your /etc/sudoers file using the "visudo" command and add the following line:

    username ALL=(root) NOPASSWD: /usr/local/bin/apt-automate

where "username" is replaced by the username you will use to remotely ssh into this machine.

3. Test update
---
Now, execute this:

``` bash
apt-get automate
```

4. Copy ssh public key to remote hosts
---
Read this [article](ssh-login-without-password.md)


5. Update from all machines
---

From your computer now you can execute this script.
It execute a ssh command for each host configured into hosts variable

``` bash
#!/bin/sh

hosts="machine1 machine2 machine3 machine4"

# Run the command on each remote host
for i in $hosts;
do
  echo $i;
  ssh $i sudo apt-automate;
done;
```

Thanks
---
http://www.linuxjournal.com/magazine/hack-and-manage-multiple-servers-efficiently
