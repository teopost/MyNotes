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
```
rsync -avz -e ssh . root@teopost.com:/var/www/apex 
```
