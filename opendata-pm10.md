Analisi recupero PM10 da Opendata arpae Emilia Romagna
======================================================

Gli opendata di arpae Emilia Romagna sulla qualità dell'aria sono qui: 

    https://dati.arpae.it

Quelli relativi ai PM10 sono qua: 

    https://dati.arpae.it/dataset/qualita-dell-aria-rete-di-monitoraggio

Il dataset che devo recuperare e' questo: 

    https://dati.arpae.it/dataset/qualita-dell-aria-rete-di-monitoraggio/resource/a1c46cfe-46e5-44b4-9231-7d9260a38e68

Per recuperare i dati in formato json (grazie al mitico CKAN) basta chiamare questa url (primi 5 risultati):

    https://dati.arpae.it/api/action/datastore_search?resource_id=a1c46cfe-46e5-44b4-9231-7d9260a38e68&limit=5

Questa lista contiene tutti i rilevamenti di tutte le stazioni nella provincia di forlì-cesena.

* La stazione di Savignano è la num: 6000031
* Il dato relativo ai PM10 è il 5

C'è una tabella completa delle stazioni qui: 

    https://dati.arpae.it/dataset/qualita-dell-aria-rete-di-monitoraggio/resource/6b1c73c6-2fa9-40b2-854a-d3f822d1451a
    
E c'è anche una legenda dei parametri disponibili qui:

    https://dati.arpae.it/dataset/qualita-dell-aria-rete-di-monitoraggio/resource/6fb8af6d-a3cc-4cf7-b098-ed95c5744cee
    
Grazie a questi dati posso inviare una query a CKAN tipo questa:

```sql
SELECT * FROM "a1c46cfe-46e5-44b4-9231-7d9260a38e68" 
WHERE station_id = '6000031' and reftime='2017-03-23T00:00:00'and variable_id=5
```

Occorre sostituire con caratteri d'escape e il gioco è fatto.

    https://dati.arpae.it/api/action/datastore_search_sql?sql=SELECT%20*%20from%20%22a1c46cfe-46e5-44b4-9231-7d9260a38e68%22%20WHERE%20station_id%20=%20%276000031%27%20and%20reftime=%272017-03-23T00:00:00%27and%20variable_id=5

Questo è il risultato:

```json 
{ "help" : "https://dati.arpae.it/api/3/action/help_show?name=datastore_search_sql",
  "result" : { "fields" : [ { "id" : "_id",
            "type" : "int4"
          },
          { "id" : "_full_text",
            "type" : "tsvector"
          },
          { "id" : "station_id",
            "type" : "int4"
          },
          { "id" : "variable_id",
            "type" : "int4"
          },
          { "id" : "reftime",
            "type" : "timestamp"
          },
          { "id" : "value",
            "type" : "float8"
          }
        ],
      "records" : [ { "_full_text" : "'00':4,5 '03/23/2017':3 '36':6 '5':1 '6000031':2",
            "_id" : 571594,
            "reftime" : "2017-03-23T00:00:00",
            "station_id" : 6000031,
            "value" : 36.0,
            "variable_id" : 5
          } ],
      "sql" : "SELECT * from \"a1c46cfe-46e5-44b4-9231-7d9260a38e68\" WHERE station_id = '6000031' and reftime='2017-03-23T00:00:00'and variable_id=5"
    },
  "success" : true
}
```

E cioè, il giorno 23 Marzo 2017, a Savignano sul Rubicone, i livello di PM10 rilevato era 36 (il limite consentito per legge è 50)

Riferimenti
-----------
* https://www.arpae.it/liberiamo/statistiche_riepilogative.asp?idlivello=822
* https://www.arpae.it/v2_aria.asp?idlivello=134&tema=valutazioni#
* http://service.arpa.emr.it/qualita-aria/bollettino.aspx?prov=FC
* https://www.arpae.it/liberiamo/dati_giornalieri_14gg.asp?idlivello=821

