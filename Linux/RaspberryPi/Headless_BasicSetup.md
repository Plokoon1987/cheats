# Headless Basic Setup
Network Configuration and SSH Access to allow Headless access to the Pi

## Assumptions
We will assumme that the MicroSD card is still connected to a Linux Operating System


## Network Connection
Use nano to edit the 'wpa_supplicant.conf' file to setup the Network Connection
```
sudo nano /media/<USERNAME>/rootfs/etc/wpa_supplicant/wpa_supplicant.conf
```
USERNAME: is the name of the user carrying out the installation

Write down the following to the bottom of file
```
network={
    ssid="Network_SSID"
    psk="Network_Password"
}
```

## SSH Access
Simply add an empty file named ssh to let the system know that ssh should be enabled
```
sudo touch /media/<USERNAME>/boot/ssh
```

## References
* https://www.raspberrypi.org/documentation/configuration/wireless/headless.md
* https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md
* https://www.raspberrypi.org/documentation/remote-access/ssh/README.md#3-enable-ssh-on-a-headless-raspberry-pi-add-file-to-sd-card-on-another-machine

