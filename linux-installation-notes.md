mkvextract
===

``` sh
sudo apt-get install -y mkvtoolnix mkvtoolnix-gui
sudo apt-get install -y libdca-utils aften
wget https://github.com/JakeWharton/mkvdts2ac3/raw/master/mkvdts2ac3.sh
chmod 777 mkvdts2ac3.sh && sudo mv mkvdts2ac3.sh /usr/bin/

# Sistemare l'orario se hai la partizione dual con windows
https://help.ubuntu.com/community/UbuntuTime
```

Example:

``` sh
Creare la traccia AC3 nuova ed eliminare la DTS: mkvdts2ac3.sh -n Some.Random.Movie.mkv
```


Thanks
---

- http://www.setupswarm.com/main/media/ubuntu-dts-to-ac3
- https://github.com/JakeWharton/mkvdts2ac3
