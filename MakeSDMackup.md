Backing up SD Cards on Mac OS X
=======

1. Insert the SD card into a USB card reader, and plug it into your Mac

2. Open Terminal.app and use the following command to list the disks attached to your Mac and identify which /dev/disk corresponds to the SD card (look for the disk that includes a partition of type Linux):

  diskutil list

3. Having found the identifier of the SD card, use the dd command to backup the SD card. For the case where the SD card is on /dev/disk1, the command is:

  umount /dev/rdisk1
  sudo dd if=/dev/rdisk1 of=/path/to/backup.img bs=1m

Notice that the dd command refers to /dev/rdisk, rather than /dev/disk. Some of the differences between these two ways of accessing a disk on Mac OS X are explained here, but the upshot is that the dd copying process is much faster if you use /dev/rdisk to access your SD card, rather than /dev/disk.

4. To restore an SD card from a backup use the following command:

  sudo dd if=/path/to/backup.img of=/dev/rdisk1 bs=1m

5. It’s also possible to create compressed SD card backups as follows:

  sudo dd if=/dev/rdisk1 bs=1m | gzip > /path/to/backup.gz

Restore from a compressed backup as follows:

  gzip -dc /path/to/backup.gz | sudo dd of=/dev/rdisk1 bs=1m
