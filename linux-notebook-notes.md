# DELL E6400

## Disable wifi blink

    sudo echo "echo \"options iwlwifi led_mode=1\" >> /etc/modprobe.d/iwlwifi.conf" | sudo bash


## Fix dropbox icon

from: http://askubuntu.com/questions/732816/xubuntu-dropbox-icon-fail

1. Remove the indicator-plugin from the panel. The dropbox icon now appears properly in the Notification Area. The network connection appears there too. But the audio control is now gone.
2. Add the xfce4-pulseaudio-plugin using synaptic. Then add it to the panel.
3. Log out, then log back in. Everything should show up properly.



## Dropbox thunar integration

To get Dropbox integration in Thunar:

    sudo add-apt-repository ppa:xubuntu-dev/extras
    sudo apt-get update
    sudo apt-get install thunar-dropbox-plugin

# DELL XPS and NEON

1. Attivare il tocco del touchpad e invertire lo scrolling

Installare i pacchetti:

    apt-get install network-manager-vpnc
    apt-get install network-manager-l2tp
    sudo apt install strongswan
    apt install libstrongswan-extra-plugins
    
vi /usr/share/X11/xorg.conf.d/40-libinput.conf 

    Section "InputClass"
            Identifier "libinput touchpad catchall"
            MatchIsTouchpad "on"
            MatchDevicePath "/dev/input/event*"
            Driver "libinput"
            Option "NaturalScrolling" "true"        
            Option "Tapping" "on"
            Option "TappingButtonMap" "lmr"
    EndSection

2. Configurare VPN L2TP/IPSEC (WEDO)

C'è un problema quando ci si collega a reti Windows.
Leggi qui: 
* https://www.fatalerrors.org/a/vpn-error-eap-unknown-authentication-type-26-naking.html

Quindi:

vi /etc/ppp/options e aggiungere in fondo al file:

    refuse-pap
    refuse-eap
    refuse-chap
    refuse-mschap
    require-mppe

Per vedere il log:

    journalctl -u NetworkManager.service -f

Impostazioni IPSEC

    Algorithm phase 1: aes128-sha1-modp1024,3des-sha1-modp1024!
    Algorithm phase 2: aes128-sha1,3des-md5


3. Configurare Cisco VPN IPSEC

TODO

4. Impostare Chrome come browser predefinito

KDE Chrome | impostazioni di sistema > Applicazioni > Associazione dei file > text > html > Ordine di preferenza delle applicazioni (spostare Chrome in cima alla lista)


