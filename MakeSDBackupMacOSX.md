Backing up SD Cards on Mac OS X
=======

From command-line
---

1. Insert the SD card into a USB card reader, and plug it into your Mac

2. Open Terminal.app and use the following command to list the disks attached to your Mac and identify which /dev/disk corresponds to the SD card (look for the disk that includes a partition of type Linux):

``` sh
diskutil list
```

3. Having found the identifier of the SD card, use the dd command to backup the SD card. For the case where the SD card is on /dev/disk1, the command is:

``` sh
umount /dev/rdisk1
sudo dd if=/dev/rdisk1 of=/path/to/backup.img bs=1m
```

Notice that the dd command refers to /dev/rdisk, rather than /dev/disk. Some of the differences between these two ways of accessing a disk on Mac OS X are explained here, but the upshot is that the dd copying process is much faster if you use /dev/rdisk to access your SD card, rather than /dev/disk.

4. To restore an SD card from a backup use the following command:

``` sh
  sudo dd if=/path/to/backup.img of=/dev/rdisk1 bs=1m
```

5. It’s also possible to create compressed SD card backups as follows:

``` sh
  sudo dd if=/dev/rdisk1 bs=1m | gzip > /path/to/backup.gz
```

Restore from a compressed backup as follows:

``` sh
  gzip -dc /path/to/backup.gz | sudo dd of=/dev/rdisk1 bs=1m
```

From Disk Utility
---

This handout will walk you through how to make a backup copy of your SD card or Compact Flash card, while retaining the integrity & structure of the footage or pictures on the card.

1. Insert your card into the card receiver, it will pop up on the finder on a Mac.

2. Open the Application folder, scroll down to the Utilities folder, open Disk Utility.

3. Select your SD card, and click New image.
 

4. Name your backup, designate where to save it and Click Save.  Make sure to give it a name that makes sense.

5. Let Disk Utility run.  The finished .dmg (disk image) will appear on the desktop.  You have now successfully made a back up copy of your card. The .dmg file that you created can now be duplicated and saved as a backup of your SD card.

6. When you need to open the backup card, double click on the .dmg (disk image), and your card will mount on the desktop.  It can be accessed like the original card.




Thanks
---
http://minordiscoveries.wordpress.com/2013/03/30/backing-up-raspberry-pi-sd-card-on-mac-os-x/
