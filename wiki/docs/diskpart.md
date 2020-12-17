
## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).


## How to build partition on disk
* `Reconnect SATA SSD to DeskPi Disk Adapter board` 
* `Format partitions and mount disks manually` - Following steps:

1. Open a terminal or press `"Ctrl+Alt+T"`.

2. Typing: "`sudo fdisk -l`" to check if the disk has been recognized or typing: "`sudo lsusb -t`", typing: "`dmesg |grep -i usb`" to make sure disk has been connected.

3. If the disk can be found by those commands, manually format and mount the partition:  
   for example: 
* `sudo fdisk /dev/sda` - sda means my first SCSI type disk which recognized by my system.
and press `p`. `p` means print current partitions that contains on the disk, and then press `n`,`n` means create a new partition, and then press `p`, means primary partion, press `1` means first partition number and then press `Enter` to set first celinder by the default number,press `Enter` again to setup the last celinder, here means to make the whole disk as one partion,after that, press `w`, `w` means `save and quit`, it will write the partion table to disk and quit. 
* Finally, you can typing: `sudo partprobe /dev/sda` in terminal.
