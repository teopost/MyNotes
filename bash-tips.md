# Git commands

## Git log human readable

```bash
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
```

```bash
# create an alias
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

git lg
```


# Bash environment

## History
```bash
MY_BASH_BLUE="\033[0;36m" #Cyan
MY_BASH_NOCOLOR="\033[0m"

export HISTSIZE=10000
export HISTTIMEFORMAT=`echo -e ${MY_BASH_BLUE}[%F %T] $MY_BASH_NOCOLOR `
```

# Others


## Test if remote TCP port is open

```bash
# using bash built-in feature
timeout 2 bash -c "</dev/tcp/www.google.com/80"; echo $?

# using telnet
telnet google.com 80

# using netcat
nc -w2 -v www.google.com 80

# using nmap
nmap -sS -O -p80,8080 www.google.com
```

## Put command in background

```
# Press ctrl+z which will stop the process running on foreground
# This will not send the process background by default, it just suspends it from running on foreground.
sleep 1000
^Z
[1]+ Stopped sleep 100
 # Put in background
bg %1
# Permit to disconnect
disown -h %1
# list of jobs
jobs
```
show this: https://www.linuxnix.com/11-fc-bg-jobs-commands-know/


## Dual boot time setting (ubuntu and windows)

```
https://help.ubuntu.com/community/UbuntuTime
```
## Create user teopost (and related group)

```
useradd -d /home/teopost -s /bin/bash  teopost
```


# Compress and uncompress
Some refs: https://linode.com/docs/tools-reference/tools/archiving-and-compressing-files-with-gnu-tar-and-gnu-zip/

## Compress folder (.tgz o tar.gz)

    tar -czvf archive_name.tgz folder_to_compress

## Uncompress folder (.tgz o tar.gz)

    tar -xvfz ./archive_name.tgz
    
## Compress list of files (.tgz o tar.gz)

    tar -czvf backup_archive.tar.gz daily_exp_FULL_PRODDB01_*
    
## Uncompress list of files (.tgz o tar.gz)

    tar -xvfz backup_archive.tar.gz

## Compress list of files (.tar.bz2)

    tar -cjvf backup_archive.tar.gz daily_exp_FULL_PRODDB01_*

## Uncompress list of files (.tar.bz2)

    tar -xvjf backup_archive.tar.bz2
    
tar  -xvjf  daily_exp_PRODDB01_19032018_070001.tar.bz2
# Find

## Find big files

``` bash

Varius: 
* find /opt  -type f -iname "*.log" -printf '%s %p\n'| sort -nr | head -10
* for i in G M K; do du -ah | grep [0-9]$i | sort -nr -k 1; done | head -n 11
* du -ahx / | sort -n -r | head -n 5
# find large files in root filesystem and exclude others
* find / -mount -type f | xargs du | sort -r -n -k 1 | head -n 10

tips: 
* https://alvinalexander.com/linux-unix/shell-script-find-command-large-files
* https://www.tecmint.com/find-top-large-directories-and-files-sizes-in-linux/

```

## Find in files

``` bash
grep -rl Cerchia ./path
```

## Find and Replace in files

``` bash
find . -name "*.txt" -print0 | xargs -0 sed -i '' -e 's/foo/bar/g'

grep --include={appconfig.properties} -rl 'tosearch' | xargs sed -i 's/tosearch/abc/g'

```
## Find old files and delete

```
# old than 5 days
find /path/to/directory/ -mtime +5 -delete
```

# SSH

## Generate and copy SSH key

You should install ssh-copy-id with brew (brew install ssh-copy-id)
``` bash
brew install ssh-copy-id
ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub root@teopost.com
```

script for putty .ppk
```
ssh-keygen -b 2048 -t rsa -f /tmp/sshkey -q -N ""
puttygen keyname -o keyname.ppk

Copy (for example with Winscp) private key into Windows machine.

Start the program called "puttygen", select "conversion" --> "Import keys" --> "your_private_key".
Save it somewhere in putty format.
Note: In order to use the converted key please create new putty session and fill the following fields:

"auto-login username" (username you wish to use as login) .
"connection" --> "ssh" --> "auth" --> "browse" (here please point to your newly generated putty key)-->
"session" --> "save".

```

## Differential copy through ssh tunnel

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

Colorized

``` bash
MY_BASH_BLUE="\033[0;34m" #Blue
MY_BASH_NOCOLOR="\033[0m"
export HISTTIMEFORMAT=`echo -e ${MY_BASH_BLUE}[%d/%m/%y %T] $MY_BASH_NOCOLOR `
``` 

References

https://www.shellhacks.com/tune-command-line-history-bash/

Speedtest
---

With curl:

```bash
curl -o /dev/null http://speedtest.wdc01.softlayer.com/downloads/test500.zip	
```

With wget

```bash
wget --output-document=/dev/null http://speedtest.wdc01.softlayer.com/downloads/test500.zip
```

With speedtest

```bash
wget -O speedtest-cli https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py
chmod +x speedtest-cli
```

Show last
---
```bash
ls  $(ls -t /u02/backupshare/prodstage/exp_dir/*.tar  | head -n1)
```


Tunnel SSH
---

``` bash
 ssh -L5984:64.137.254.104:5984 user@mazinga
``` 
Remap local port 5984 for remote mazinga host on port 5984

 ``` bash
http://localhost:5984/_utils/index.html
 ``` 
 
# Colors

```bash
export TERM=xterm-color
export GREP_OPTIONS='--color=auto' GREP_COLOR='1;32'
export CLICOLOR=1
export LSCOLORS=ExFxCxDxBxegedabagacad
```
