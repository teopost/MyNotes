Creare pivot con Libreoffice
============================

1. Installare il driver JDBC di Microsoft
-----------------------------------------
Scaricarlo dall'indirizzo: 

http://www.microsoft.com/it-it/download/details.aspx?id=11774

Nota: il driver jtds con LibreOffice non funziona

* Mettere il file jar nella cartella /Library/Java/Extensions

2. Configurare LibreOffice
---------------------------
* Aprire LibreOffice andare nelle *Preferenze/LibreOffice/Avanzato*.
* Cliccare *Percorso classe*
* Cliccare *Aggiungi archivio* e selezionare il file jar del driver
* Riavviare LibreOffice

3. Creare un nuovo database
---------------------------
In libreoffice non si possono salvare le connessioni db dentro un foglio di calcolo.
Occorre salvarle in un file di Base.


url string connection:
sqlserver://cork:1433;databasename=CRM;user=sa;password=apice

Driver name:
com.microsoft.sqlserver.jdbc.SQLServerDriver



* Enable Guest User in System Preferences > Users & Groups
* Open Terminal

```bash
sudo bash
cd /System/Library/User\ Template
cp -a English.lproj English.lproj.orig
```
