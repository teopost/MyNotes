Creare pivot con Libreoffice su Mac
===================================

1. Installare il driver JDBC di Microsoft
-----------------------------------------
Il driver jtds con LibreOffice non funziona

Scaricare quello Microsoft dal seguente indirizzo: 

    http://www.microsoft.com/it-it/download/details.aspx?id=11774

Mettere il file jar nella cartella /Library/Java/Extensions

2. Configurare LibreOffice
---------------------------
* Aprire LibreOffice andare nelle *Preferenze/LibreOffice/Avanzato*.
* Cliccare *Percorso classe*
* Cliccare *Aggiungi archivio* e selezionare il file jar del driver
* Riavviare LibreOffice

3. Creare un nuovo database
---------------------------
In libreoffice non si possono salvare le connessioni db dentro un foglio di calcolo.
Occorre salvarle in un file di Base esterno

* Cliccare File/Nuovo/Database
* Selezionare driver JDBC
* Mettere i seguenti parametri:

    url string connection: sqlserver://cork:1433;databasename=CRM;user=sa;password=***
    Driver name: com.microsoft.sqlserver.jdbc.SQLServerDriver

4. Creare una Ricerca sui dati
==============================
Per mostrare i dati nella pivot bisogna esporli da base con una query
Questo per evitare un errore *sql sintax*
* In Base creare nuova ricerca
* Selezionare la tabella interessata o farlo attraverso una query

5. Creare la tabella pivot
==========================
* Aprire LibreOffice
* Andare in Dati
* Scegliere Crea pivot
* Scegliere il database salvato il precedenza
* Scegliere il tipo ricerca
* Scegliere la ricerca salvata in Base
