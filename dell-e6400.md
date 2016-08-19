Disable wifi blink
---

    sudo echo "echo \"options iwlwifi led_mode=1\" >> /etc/modprobe.d/iwlwifi.conf" | sudo bash


Fix dropbox icon
---

from: http://askubuntu.com/questions/732816/xubuntu-dropbox-icon-fail

1. Remove the indicator-plugin from the panel. The dropbox icon now appears properly in the Notification Area. The network connection appears there too. But the audio control is now gone.
2. Add the xfce4-pulseaudio-plugin using synaptic. Then add it to the panel.
3. Log out, then log back in. Everything should show up properly.



Dropbox thunar integration
---

To get Dropbox integration in Thunar:

    sudo add-apt-repository ppa:xubuntu-dev/extras
    sudo apt-get update
    sudo apt-get install thunar-dropbox-plugin
