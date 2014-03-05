Find in files
---

```
grep -rl Cerchia ./path
```


Find and Replace in files
---
```
find . -name "*.txt" -print0 | xargs -0 sed -i '' -e 's/foo/bar/g'
```
