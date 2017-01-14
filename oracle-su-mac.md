Install cx_Oracle on Mac
---

Creare la cartella /Users/<utente>/oracle e metterci dentro:

```bash
instantclient-basic-macos.x64-11.2.0.4.0.zip
instantclient-sdk-macos.x64-11.2.0.4.0.zip
instantclient-sqlplus-macos.x64-11.2.0.4.0.zip
```

scompattarli

```bash
unzip instantclient-basic-macos.x64-11.2.0.4.0.zip
unzip instantclient-sdk-macos.x64-11.2.0.4.0.zip
unzip instantclient-sqlplus-macos.x64-11.2.0.4.0.zip
```

Andare nella cartella che lo scompattamento crea

```bash
cd /Users/<utente>/instantclient11_2
```

Creare i 2 seguenti link simbolici (controllare la versione delle dll)

```bash
ln -s libclntsh.dylib.11.1 libclntsh.dylib
ln -s libocci.dylib.11.1 libocci.dylib
```

Eseguire la seguente fix

```
curl -O https://raw.githubusercontent.com/kubo/fix_oralib_osx/master/fix_oralib.rb
ruby fix_oralib.rb --absolute-path
```

Aggiungere nel .bash_profile se seguenti righe

```
export ORACLE_HOME=/Users/teopost/oracle/instantclient_11_2
export DYLD_LIBRARY_PATH=$ORACLE_HOME
export SQLPATH=$ORACLE_HOME
export LD_LIBRARY_PATH=$ORACLE_HOME
export PATH=$PATH:$ORACLE_HOME
```

source /Users/<utente>/.bash_profile

Installare cx_Oracle
---

Scaricare il sorgente di cx_Oracle (cx_Oracle-version.tar.gz) nella cartella Doenloads

```bash
cd cx_Oracle-version
sudo -E pip install cx_Oracle
```


Riferimenti
---
* https://github.com/kubo/fix_oralib_osx
