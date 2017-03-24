Analisi accesso ai dati su THE FLEXX ITALIA
---------------------------------------------

La prima cosa che viene schelta dall'operatore è il CATALOGO 

    -- Lista dei cataloghi (cod_catalogo: 3681, 3701)
    SELECT * FROM dbo.API_MOB_TAGLIE_CATALOGHI

Ogni catalogo contiene un suo elenco di articoli 

    -- Cataloghi articoli (recupero 206987)
    SELECT * FROM VW_API_MOB_TAGLIE_CATALOGHI_ART 
    WHERE COD_CATALOGO = 3681 
    AND COD_ARTICOLO = 'C1023_06'

Dopo la selezione del catalogo e dell'articolo, viene mostrata la lista delle combinazioni possibili con cui puo' essere venduto quell'articolo. 
Tale lista di combinazioni è riportata nella tabella delle regole

    SELECT * FROM VW_API_MOB_REGOLE

In questa tabella, per uno specifico articolo appartenente ad uno specifico catalogo, è riportata:

1. Il COD_LISTA_MATERIALE_COMB
2. La descrizione della scelta che compare nell'interfaccia DES_SCELTA1

Il COD_LISTA_MATERIALE_COMB contiene il materiale con è possibile vendere l'articolo.
Questa tabella ha una tabella figlia con la lista dei colori disponibili per quel materiale.

MATERIALI
---------
COD_LISTA_MATERIALE_COMB
DES_MATERIALE
COD_LISTA_COLORI
