Disable wifi blink
---

    echo "echo \"options iwlwifi led_mode=1\" >> /etc/modprobe.d/iwlwifi.conf" | sudo bash
