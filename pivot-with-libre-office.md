Create PivotTable with Libreoffice on Mac
===================================

1. Install the JDBC driver from Microsoft
-----------------------------------------
The driver jtds with LibreOffice does not work

Download to Microsoft at the following address :

    http://www.microsoft.com/it-it/download/details.aspx?id=11774

Put the jar file in the folder /Library/Java/Extensions

2. Configure LibreOffice
------------------------
* Open LibreOffice, go into *Preferenze/LibreOffice/Avanzato*.
* Click on *Percorso classe*
* Click on *Aggiungi archivio* and select the jar file of the driver
* Restart LibreOffice

3. Create a new database
------------------------
In libreoffice can not save db connections in a spreadsheet.
You must save them in a file outside of Base

* Click File/Nuovo/Database
* Select driver JDBC
* Put this parameters:
```
url string connection: sqlserver://cork:1433;databasename=CRM;user=sa;password=***
Driver name: com.microsoft.sqlserver.jdbc.SQLServerDriver
```

4. Create query
---------------
To view the data in the pivot must expose them to the Base with a query (this is to avoid *sql syntax error*)
* Create a new query on Base
* Select the query

5. Create pivot table
---------------------
* Open LibreOffice
* Go to *Dati*
* Select *Crea pivot*
* Select the database
* Select query type
* Select query stored in Base file
