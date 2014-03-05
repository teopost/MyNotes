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
