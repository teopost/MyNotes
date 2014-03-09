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

Differential copy through ssh tunnel
--- 

Copy all local files (subfolder included) to remote server
``` bash
rsync -avz -e ssh . root@teopost.com:/var/www/apex 
```

Generate and copy SSH key
---

You should install ssh-copy-id with brew (brew install ssh-copy-id)
``` bash
brew install ssh-copy-id
ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub root@teopost.com
```
