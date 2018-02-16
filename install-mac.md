# Anteprima file SQL

1. Andare in /Users/teopost/Library/QuickLook
2. Scaricare il file: 
wget https://gist.github.com/teopost/a6bbfc210d58f9658d210354b78dc28d

3. Il file scaricato rinominarlo in SQLQuickLook.qlgenerator
4. Riavviare quicklook ```qlmanage -r```
5. Riavviare Finder ```killall Finder```
6. Se vuoi aggiungere altre estensioni lo puoi fare nel file Info.plis in:

 ```xml
 <key>public.filename-extension</key>
 <array>
     <string>sql</string>
     <string>[additional_extension]</string>
 </array>
 ```
 
# Riferimenti

http://www.deversus.com/blog/2010/12/web-developer-tip-preview-sql-files-in-mac-os-quick-look/

# Problemi con Hostname

Verifica se è settato l'hostname

```bash
scutil --get HostName
```

Se non è disponibile HostName, vuol dire che probabilmente proviene dal DNS o dal DHCP.

Imposta l'hostname con:

```bash
sudo scutil --set HostName 'yourHostName'
```


