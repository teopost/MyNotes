# Note di Rilascio

## Rel. 3.0.0 del 09/09/2013

### Anomalie

**_Corretto bug su salto pagina dei reports pdf generati_** - (rif: 8750)

E' stato reso dinamico il numero degli elementi nel dettaglio del report

**_Bug filtro documenti in schede_** - (rif: 8837)

Eliminato crash in selezione tipi documento se non presenti documenti

**_Mappa Clienti: corretto controllo su ultimo ordine effettuato_** - (rif: 8847)

Ora il controllo su "ultimo ordine effettuato" valorizza il colore del pin correttamente

### Novità

**_Aggiunta funzionalità di ricerca alla galleria._** - (rif: 8373)

Aggiunta funzionalità di ricerca alla galleria.

**_Interfaccia LM Partner_** - (rif: 8829)

Nascosti i pulsanti in alto che non servono.
Aggiunto pulsante per configurare i parametri a livello di progetto

**_Aggiunta presa ordini da foto._** - (rif: 8846)

Aggiunta presa ordini da item foto (preview item a tutto schermo).

**_Miglioramenti login/logout_** - (rif: 8857)

- non è possibile rientrare nell'applicazione una volta fatto il logout/esci
- altri miglioramenti validazione login

### Modifiche

**_Non viene ricalcolato il prezzo automatico se viene imputato un prezzo da parte dell'utente_** - (rif: 8809)

In inserimento ordine viene disabilitato il caricamento di default degli sconti o del prezzo dopo aver modificato la quantita se, almeno una volta, i prezzi o gli sconti sono stati modificati direttamente dall'utente. In questo caso questi non vengono più ricalcolati.

-------

## Rel. 2.9.0 del 05/07/2013

### Anomalie

**_Risolto problema con destinazioni diverse._** - (rif: 8850)

Risolto problema con destinazioni diverse.

-------

## Rel. 2.8.0 del 27/06/2013

### Anomalie

**_Corretto posizionamento in selezione giro visite_** - (rif: 8807)

Ora la lista dei clienti in inserimento ordine, nel caso di selezione giro visite, è correttamente posizionata alla sezione del giorno corrente

**_Inibita selezione clienti bloccati in girovisite_** - (rif: 8808)

Anche nel popup del girovisite non è possibile prendere ordini su clienti bloccati.

**_Sistemata regressione galleria_** - (rif: 8811)

Dal catalogo, apro una foto, scorro in avanti per una decina di foto, fine, mi posiziona nella foto su cui mi sono fermato, non più su quella di partenza.

**_Incassi non visibili dopo aggiornamento_** - (rif: 8823)

Ora si vedono gli incassi salvati associati a scadenze, anche dopo la ri-sincronizzazione delle scadenze.


### Novità

**_Blocchi modifica prezzi o sconti per utente_** - (rif: 8579)

Vengono gestiti dei parametri lato license manager che impediscono la modifica di prezzi o sconti proposti dal sistema

**_Aggiunto nuovo modulo: Reports_** - (rif: 8720)

Aggiunto nuovo modulo contenente i report di BI.

**_Cambiato il messaggio di errore nel caso di "Server non raggiungibile"_** - (rif: 8777)

Ora questo tipo di errore viene mappato con un errore comprensibile per l'utente finale e non con "errore generico".

**_Estesa la ricerca dei clienti_** - (rif: 8789)

Nella ricerca del cliente o fornitore, oltre che per codice e descrizione, aggiunta ricerca per i seguenti attributi: 
CAP, Provincia, Città, Indirizzo.

**_Miglioramenti UI in modulo CRM_** - (rif: 8810)

Rivista gestione filtri offerte (leads, stati, date).
Miglioramenti visuali nella lista delle offerte.
Inserito controllo obbligatorietà ragione sociale e gestione note in "popover" per inserimento nuovo lead.


**_Invio notifiche push da am_** - (rif: 8828)

Sono state implementate alcune modifiche al form di invio notifiche push da am:
1. Aggiunta l'opzione tutti per mandare la notifica a tutti quanti.
2. Aggiunto un messaggio che indica l'avvenuto invio
3. Gestiti errori su contenuto messaggio

### Modifiche

**_Inclusa visibilita clienti anche per agenti associati a destinazioni_** - (rif: 8840)

In fase di estrazione dati dal connettore, ora vengono inclusi anche i clienti associati ad agenti collegati alle destinazioni.


-------

## Rel. 2.7.0 del 07/06/2013

### Anomalie

**_Scheda Prodotti: risolto problema di visualizzazione dati_** - (rif: 8783)

Quando la descrizione dell'articolo e' molto lunga, i prezzi venivano sovrascritti nei dettagli "ultimi prezzi di acquisto e vendita"

**_Filtro in ordini veloci_** - (rif: 8797)

Corretto il filtro per destinazione

### Modifiche

**_Cambiata dicitura "Uguale sede" con "Nessuna destinazione diversa"_** - (rif: 8780)

Nel form ordine, quando si sceglie destinazioni diverse ora viene proposto:
- "Nessuna destinazione diversa" (default, in inserimento)
- Tutte le altre destinazioni diverse associate al cliente

Da ricordare che se viene preso un ordine da storico, la destinazione selezionata è l'ultima destinazione (quella presente sullo storico).

-------

## Rel. 2.6.0 del 31/05/2013

### Novità

**_CRM:  nuova funzione Schede Leads_** - (rif: 8717)

Aggiunta nuova funzione Schede Leads in modulo CRM

**_CRM: Aggiunta nuova funzione Offerte_** - (rif: 8719)

Possibilità di vedere le offerte raggruppate per lead. Varie possibilità di filtro ed ordinamento.

**_CRM: Nuovi Leads_** - (rif: 8743)

Aggiunta nuova funzione Nuovi Leads in modulo CRM.

**_Giro visite: selezione cliente_** - (rif: 8753)

Aggiunta possibilità di selezionare il cliente con cui viene effettuato l'ordine attraverso il giro viste.

**_Scheda prodotti: miglioramenti visualizzazione dati_** - (rif: 8779)

Ad esempio nella lista prodotti aggiunta una gestione ordinamento (simile a quella di ordini veloci)


-------

## Rel. 2.5.0 del 24/05/2013

### Anomalie

**_Risolti problemi con dimensioni immagini anteprima in lista prodotti_** - (rif: 8752)

Nel caso ci siano immagini con dimensioni inferiori al limite minimo stabilito vengono comunque gestite correttamente le dimensioni delle immagini di anteprima

### Novità

**_Miglioramenti dei downloads per la Galleria_** - (rif: 8657)

- gestione download thumbnail asset come file (non cache http)
- migliorata velocità di cancellazione di tutti i file
- migliorata velocità inizializzazione iniziale

**_Aggiunta informazioni in liste Clienti Fornitori_** - (rif: 8734)

L'elenco dei clienti e dei fornitori, nel modulo schede, si presentano come quello
del modulo order, con l'indirizzo e le altre informazioni visibili in lista.

**_Aggiunta filtro in Incassi_** - (rif: 8735)

Aggiunto nel filtro, oltre che incassate e da
incassare, anche le scadute e non scadute

**_Ordinamento righe in ordini veloci_** - (rif: 8746)

Impostato, come standard, l'ordinamento per data/discendente.

**_Modifiche visualizzazione dati relativi a sconti._** - (rif: 8759)

- Nella lista degli ordini veloci è possibile vedere se sono presenti sconti non nulli, ed eventualmente ispezionarli in dettaglio tramite appostito bottone.
- Lo sconto totale da listini non tiene conto degli ScontiFull.

**_Aggiunti dati visualizzazione in ordini salvati_** - (rif: 8775)

Vengono visualizzati um e qta ordine, sia nella lista che nel report.

-------

## Rel. 2.4.0 del 19/04/2013

### Anomalie

**_Ottimizzata apertura form ordine._** - (rif: 8712)

Corretta la logica dell'apertura del form ordine, che poteva causarne una apertura lenta.

**_Risolta anomalia check prezzo minimo di vendita._** - (rif: 8745)

Risolta anomalia check prezzo minimo di vendita.

### Novità

**_Aggiunta funzionalità di sharing alla galleria._** - (rif: 8613)

Lo sharing è abilitato per:
- Immagini (Email, Facebook, Twitter)
- Pdf (Email)
- Video (Email)
Limite massimo per ogni file fissato a 20 Mb.

-------

## Rel. 2.2.0 del 09/04/2013

### Anomalie

**_Destinazioni in Ordine: selezione_** - (rif: 8670)

L'utente può ora selezionare nessuna destinazione differente da quella della sede

**_Scheda Fornitore: totale fatturato_** - (rif: 8715)

Nella videata dei fornitori é stato inserito il totale fatturato come nella videata dei clienti

-------

## Rel. 2.3.0 del 05/04/2013

### Anomalie

**_Fix Sconti per articolo_** - (rif: 8713)

Se si fa il "tap" più volte sul Tab Sconti non si duplicano i "buttons" di filtro.

### Novità

**_Aggiunto check quantità minima ordinabile per colli_** - (rif: 8722)

Aggiunto check che controlla che le quantità ordinate inserite siano un multiplo rispetto alla quantità per colli, attivabile dai parametri di progetto.

### Modifiche

**_Ottimizzate dimensioni immagini di anteprima_** - (rif: 8710)

Nel caso ci siano immagini con dimensioni inferiori al limite minimo stabilito vengono comunque gestite correttamente le dimensioni delle immagini di anteprima.

-------

## Rel. 2.1.0 del 22/03/2013

### Anomalie

**_Risolto Crash su uscita form ordini_** - (rif: 8610)

Descrizione problema:
se si salva un ordine che ha quantita' zero, viene mostrata la popup che avvisa che la quantita' non deve essere zero;
se si chiude il form l'app va in crash.

**_Cambiata visualizzazione descrizione destinazione nel form ordine._** - (rif: 8616)

Cambiata visualizzazione descrizione destinazione nel form ordine. Vengono mostrati:
-ipad: 
ragione sociale e città 
-iphone: 
ragione sociale

**_Risolto problema in assegnazione agente in import ordini_** - (rif: 8651)

In Business, un agente puo' essere pricipale o secondario (es: subagente).
Quando un agente secondario effettuava un ordini, veniva riportato nella testata dell'ordine ma non c'era evidenza dell'agente 1.
Se l'ordine di inserisce da interfaccia invece viene correttamente riportato l'agente 1 come primario e il 2 come secondario.
Ora l'import si comporta come se l'ordine venirre inserito da interfaccia.
Viene cioe' verificato se l'agente che ha inserito ordine e' primario o secondario.
nel primo caso viene messo nella testata dell'ordine, nel secondo caso viene importato come agente secondario e nel campo agente primario dell'ordine viene inserito l'agente 1.

**_Riviste instestazioni dettaglio contatto in Schede cli/for_** - (rif: 8655)

Modificate intestazioni campi: email,telefono,cellulare ed indirizzo per dettaglio contatto di Clienti e Fornitori

**_Risolto problema su filtro documenti_** - (rif: 8678)

In scheda cli/for rivista la logica di presentazione dei dati ammissibili del filtro documenti

### Novità

**_Aggiunta visualizzazione ordini inviati._** - (rif: 8520)

Aggiunti ordini inviati nella scheda ordini, modulo ordini, ordini inviati.
Si possono vedere raggruppati per data e poi ordinati per cliente.
Aggiunta funzionalità di ricerca (per cliente) sia agli ordini salvati che a quelli inviati.

**_Dati aggiuntivi in scheda cliente_** - (rif: 8562)

Aggiunta dettaglio sconti

**_Aggiunto avviso durante il logout o il cambio progetto._** - (rif: 8566)

Aggiunto avviso durante il logout o il cambio progetto, che avvisa l'utente nel caso di ordini salvati, clienti modificati e note cliente non ancora inviate.

**_Modifiche allo storico ordini (Ordini veloci)_** - (rif: 8605)

Aggiunto nuovo filtro per destinazione cliente. Le destinazioni proposte sono le destinazioni associate al cliente di lavoro.
Possibilità di prendere ordini da storico, con i prezzi e sconti da listino.
Corretta gestione della unità di misura secondaria.

**_Implementata raccolta ordine per utente cliente._** - (rif: 8606)

Implementata raccolta ordine per utente cliente.

**_Aggiunto report pdf a modulo ordini inviati_** - (rif: 8615)

Aggiunto report pdf a modulo ordini inviati.

**_Aggiunto cod articolo in storico ordini._** - (rif: 8623)

Aggiunto cod articolo in storico ordini.

**_Visualizzazione omaggio in riga ordine_** - (rif: 8626)

Nel caso in cui un ordine sia un omaggio, il prezzo e gli sconti non vengono mostrati, e viene mostrata la descrizione della tipologia dell'omaggio.

**_Aggiunto pulsantino X nel campo descrizione articolo._** - (rif: 8647)

Aggiunto pulsantino X nel campo descrizione articolo.

**_Ordine di visualizzazione articoli in catalogo_** - (rif: 8648)

È stata fatta la modifica nella galleria in modo da ordinare gli elementi per titolo in automatico il più possibile uguale in Windows file system.

**_Aggiunto nuova impostazione per regolare il raggruppamento dei pin nella mappa._** - (rif: 8649)

Aggiunto nuovo setting per permettere all'utente di personalizzare il livello di raggruppamento dei pin relativi ai clienti sulla mappa.

**_Dati aggiuntivi in scheda prodotti_** - (rif: 8650)

Aggiunta dettaglio sconti

**_Dati aggiuntivi in scheda fornitore_** - (rif: 8656)

Aggiunta dettaglio sconti

**_Modificato download delle thumbnail della galleria_** - (rif: 8672)

I thumbnail della galleria ora sono scaricati e memorizzati nella memoria del device.
Questa modifica fa in modo che l'utente possa vedere tutti i thumbnail anche in condizioni di mancanza di connessione.

**_Nuova gestione delle unità di misura e confezioni._** - (rif: 8674)

Introdotta la gestione delle confezioni e unità di misura "come business".
La procedura operativa per inserire un nuovo ordine sarà:
1- si seleziona l'unità di misura
2- si inserisce la quantità, riferita all'unità di misura precedentemente scelta
3- in automatico vengono calcolati e visualizzati um, qta e prezzo espressi in unità di misura principale (il prezzo è imputabile)
4- si inseriscono eventuali sconti.


