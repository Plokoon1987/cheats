# OS Install
Shows how to install a Raspbian on a "SD Card"

## Requirements:
* MicroSD Card
* Raspbian or any other OS downloaded from [Ref_01]( https://www.raspberrypi.org/downloads/)
      (use 'sha256sum <IMAGE_FILE>' or 'sha256sum <ZIP_FILE>' To verify downloaded file)

Requirements:
  - MicroSD Card
  - Raspbian or any other OS downloaded from 'Ref_01'
      (use 'sha256sum <IMAGE_FILE>' or 'sha256sum <ZIP_FILE>' To verify downloaded file)

In Terminal:
  lsblk
    -Note: Write down name of MicroSD Card (I think that it cannot be sda or sr0),
           Let's assume that the MicroSD Card is CARD_NAME (i.e. 'mmcblk0')

If using .img file, run in Terminal:
  dd bs=4M if=<IMAGE_FILE> of=/dev/<CARD_NAME> conv=fsync
  i.e:
    sudo dd bs=4M if=2018-06-27-raspbian-stretch-lite.img of=/dev/mmcblk0 status=progress conv=fsync

If .img is within a ZipFile, run in Terminal:
  unzip -p <ZIP_FILE> | sudo dd of=/dev/<CARD_NAME> bs=4M conv=fsync
  i.e:
    unzip -p 2018-06-27-raspbian-stretch-lite.zip | sudo dd of=/dev/mmcblk0 bs=4M status=progress conv=fsync

## References
* Ref_01: https://www.raspberrypi.org/downloads/
* Ref_02: https://www.raspberrypi.org/documentation/installation/installing-images/linux.md
