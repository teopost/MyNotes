Dual boot time setting (ubuntu and windows)
--
        https://help.ubuntu.com/community/UbuntuTime

Find in files
---

``` bash
grep -rl Cerchia ./path
```


Find and Replace in files
---

``` bash
find . -name "*.txt" -print0 | xargs -0 sed -i '' -e 's/foo/bar/g'
```

Generate and copy SSH key
---

You should install ssh-copy-id with brew (brew install ssh-copy-id)
``` bash
brew install ssh-copy-id
ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub root@teopost.com
```

Differential copy through ssh tunnel
--- 

Copy all local files (subfolder included) to remote server. Thanks to http://www.linuxawy.org/node/12
``` bash
rsync -avzr -e ssh * root@teopost.com:/var/www/apex 
```

Add date and time to bash history
---
If the HISTTIMEFORMAT is set, the time stamp information associated with each history entry is written to the history file, marked with the history comment character. Defining the environment variable as follows:

``` bash
$ HISTTIMEFORMAT="%d/%m/%y %T "
```

or 

``` bash
$ echo 'export HISTTIMEFORMAT="%d/%m/%y %T "' >> ~/.bash_profile
```

Where:

    %d - Day
    %m - Month
    %y - Year
    %T - Time

Sample output

    ....
    ..
      986  11/03/10 04:31:36 memcached-tool  10.10.28.22:11211 stats
      987  11/03/10 04:31:36 w
      988  11/03/10 04:31:37 iostat
      989  11/03/10 04:31:37 top
      990  11/03/10 04:31:37 at
      991  11/03/10 04:31:38 atop
      992  11/03/10 04:31:40 collectl
      993  11/03/10 04:31:41 grep CPU /proc/cpuinfo
      994  11/03/10 04:31:45 vmstat 3 100
      995  11/03/10 04:31:55 sar -W -f /var/log/sa/sa12
    ....
    ..

This is my setting

``` bash
export HISTSIZE=100000
export HISTTIMEFORMAT="%d/%m/%y %T "
 ```
