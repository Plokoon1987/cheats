Refs:
  https://www.raspberrypi.org/documentation/configuration/wireless/headless.md
  https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md
  https://www.raspberrypi.org/documentation/remote-access/ssh/README.md#3-enable-ssh-on-a-headless-raspberry-pi-add-file-to-sd-card-on-another-machine


*** Connecting  RaspberryPi to the Network ***
Note: All is relative to the 'rootfs' partition in MicroSD Card where OS
      is installed

In Terminal:
  sudo nano /media/froylan/rootfs/etc/wpa_supplicant/wpa_supplicant.conf

  Go to the bottom of the file and add the following:

    network={
        ssid="Network_SSID"
        psk="Network_Password"
    }


*** Allowing SSH Access***
Note: All is relative to the 'boot' partition in MicroSD Card where OS
      is installed

In Terminal:
  sudo vim /media/froylan/boot/ssh (and simply save file with 'wq')