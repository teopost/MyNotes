
## XML Indentation

For XML files, I use this command

```bash
:1,$!xmllint --format --recover - 2>/dev/null
```

note: You need to have xmllint installed (package libxml2-utils)

(Source : http://ku1ik.com/2011/09/08/formatting-xml-in-vim-with-indent-command.html )

