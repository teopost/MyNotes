
## XML Indentation

For XML files, I use this command

```bash
:1,$!xmllint --format --recover - 2>/dev/null
```

note: You need to have xmllint installed (package libxml2-utils)

(Source : http://ku1ik.com/2011/09/08/formatting-xml-in-vim-with-indent-command.html )

## Code indention

The master of all commands is

```
gg=G
```

This indents the entire file!

And below are some of the simple and elegant commands used to indent lines quickly in Vim or gVim.

To indent the all the lines below the current line

```
=G
```

To indent the current line

```
==
```

To indent n lines below the current line

```
n==
```

For example, to indent 4 lines below the current line

```
4==
```

To indent a block of code, go to one of the braces and use command

```
=%
```

