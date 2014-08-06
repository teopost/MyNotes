Backup smb.cfg
---
Copy /etc/samba/smb.cfg in /etc/samba/smb.cfg_ORI

```bash
cp /etc/samba/smb.cfg /etc/samba/smb.cfg_ORI
```

Edit smb.cfg
---
Delete file content and paste this :

```
[global]
netbios name = tangeri-linux
workgroup = WORKGROUP
server string = Public File Server
security = user
map to guest = bad user
guest account = smbguest


[public]
writeable = yes
path = /stage/shared
guest ok = yes
read only = no

```

Test
---
Execute testparm to check sintax

```bash
$ testparm
````

Restart service
---

```bash
$ service samba restart
````
