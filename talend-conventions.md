
Talend ETL Conventions
===

The default mapping of data types is controlled through Window > Preferences > Talend > Specific Settings > Metadata of Talend. 

 In your case, you want to edit the <dbToTalendTypes> section in mapping_Sybase.xml. 
 Under <dbType type="NUMERIC"> change the default to BigDecimal.  

Note that this only affects how the Talend Data Type in the schema is initially
 set when you retrieve it and you can manually change any column afterwards.

To convert 
 double to BigDecimal, just use BigDecimal.valueOf(<your double>).
 floats, use BigDecimal.valueOf(<your float>.doubleValue()).
Last edited by alevy (2011-09-22 00:14:37)





http://www.talendforge.org/forum/viewtopic.php?id=15502





da: STRING a BIGDECIMAL

   (BigDecimal)((DecimalFormat)globalMap.get("bdfmt")).parse(row5.IMPORTO);   


da: LONG a STRING

   Convertire iun long in string: (String)row5.NUMREG.toString(); 

da: INTEGER a BIGDECIMAL
    new BigDecimal(Integer.toString(row1.IND_LISTINO)); 

da: STRING a INTEGER
    Integer.parseInt(row1.QUANTITA)


(row1.DATACONS==null)?null:TalendDate.parseDate("ddMMyyyy",row1.DATACONS) 
(row1.DES_GR_STAT2=="")?null:(row1.DES_GR_STAT2)  



Problema 65 k:  http://www.talendforge.org/forum/viewtopic.php?id=16444


http://bekwam.blogspot.com/2011/10/applying-contexts-to-talend-open-studio.html

http://www.youtube.com/watch?v=48n4dixL8X0


http://powerupbi.com/talend/

http://www.tumblr.com/tagged/talend





componenti
------------
http://www.talendforge.org/exchange/tos/index.php?view=compact

link interessanti
----------------------
http://www.dataprix.net/en/blogs/respinosamilla/product-dimension-etl-load-more-examples-talend-using-logs-metrics-and-statisti
http://thinkinginsoftware.blogspot.com/2010/09/etl-importing-data-with-talend.html
http://richardlog.com/post/15939924496/putting-talend-open-studio-projects-under-version
http://www.dariopardo.com/talend-open-studio/svnintegration/
http://bekwam.blogspot.com/
http://www.talendforge.org/forum/viewtopic.php?id=5974


http://www.talendforge.org/bugs/view.php?id=9694
http://bekwam.blogspot.it/2011/05/to-iterate-or-flow-in-talend-open.html


Se leggo dati da access per leggere le accentate usare :
System.setProperty("file.encoding","ISO-8859-1");

ACCESS SHORT TO INTEGER
(int)row1.Codice 

from DOUBLE to INTEGER
row1.EtaM.intValue() 
