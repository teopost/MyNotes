Using mkvextract
===

``` sh
sudo apt-get install -y mkvtoolnix mkvtoolnix-gui
sudo apt-get install -y libdca-utils aften
wget https://github.com/JakeWharton/mkvdts2ac3/raw/master/mkvdts2ac3.sh
chmod 777 mkvdts2ac3.sh && sudo mv mkvdts2ac3.sh /usr/bin/

```

Examples:

``` sh
Creare la traccia AC3 nuova ed eliminare la DTS: mkvdts2ac3.sh -n Some.Random.Movie.mkv
```

http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvpropedit.html
http://linux.die.net/man/1/mkvextract

Cambiare il flag default dalla prima alla seconda traccia

    mkvpropedit Che\ bella\ giornata\ \(copia\).mkv --edit track:2 --set flag-default=0 --edit track:3 --set flag-default=1


Cambiare il flag forced a true nella seconda traccia audio
    
    mkvpropedit Che\ bella\ giornata\ \(copia\).mkv  --edit track:3 --set flag-forced=1

Disabilitare una traccia

    mkvpropedit Che_bella_giornata.mkv --edit track:3 --set flag-enabled=0

Mettere il default flag a 1 (non devono essercene altri pero)

    mkvpropedit Che_bella_giornata.mkv --edit track:3 --set flag-default=1

Mostra l'elenco delle tracce

    mkvmerge -i Che_bella_giornata.mkv

    Track ID 1: video (V_MPEG4/ISO/AVC)
    Track ID 2: audio (A_DTS)
    Track ID 3: audio (A_AC3)
    Track ID 4: subtitles (S_TEXT/UTF8)
    Track ID 5: subtitles (S_TEXT/UTF8)
    


Estrai la traccia 3 e mettila nel file audio.ogg
    
    mkvextract tracks Che_bella_giornata.mkv  2:audio.ogg


Cambia l'ordine delle traccia 


    mkvmerge -o "/home/teopost/Video/ORIGINALI/Che_bella_giornata_OUT.mkv" \
    "/home/teopost/Video/ORIGINALI/Che_bella_giornata.mkv" --track-order "0:1,0:3,0:4,0:5"




Thanks
---

- http://www.setupswarm.com/main/media/ubuntu-dts-to-ac3
- https://github.com/JakeWharton/mkvdts2ac3
