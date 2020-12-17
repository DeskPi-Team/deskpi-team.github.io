## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## Disk drive Issues 
### Why does my SSD hard drive not work normally after my Logitech wireless mouse and keyboard dongle is connected to DeskPi?  

* Because the 2.4G frequency used by Logitech's mouse and keyboard interferes with DeskPi's USB transfer interface, it will cause the disk to work in an unstable state. This problem with Logitech's keyboard and mouse also occurs on desktop computers. The current solution is best to replace the wireless keyboard and mouse or use a wired keyboard and mouse.

### Why is it normal when I start the Raspberry Pi with a TF card, but the SATA SSD hard disk cannot appear on the desktop? 

* The disk cannot be displayed on the desktop may be caused by the following reasons:
* `Hardware connection` - The hardware is not connected properly, such as forgetting to install the USB adapter.
* `Not Initialized Before` - The SATA SSD hard disk is a RAW Disk, the brand new one has not been partitioned, formatted, or mounted.
* `Unavailable file system format` - file sytem format not recognized by the Linux system is used, for example: NTFS 

### Solution and diagnostic 
* `Reconnect SATA SSD to DeskPi Disk Adapter board` 
* `Format partitions and mount disks manually` - Following steps:
1. Open a terminal or press l"Ctrl+Alt+T".
2. Typing: "sudo fdisk -l" to check if the disk has been recognized or typing: "sudo lsusb -t", typing: "dmesg |grep -i usb" to make sure disk has been connected.
3. If the disk can be found by those commands, manually format and mount the partition:  
 for example: 
4. `sudo fdisk /dev/sda` - sda means my first SCSI type disk which recognized by my system.
5. `p` - typing `p` means print current partions that contains on the disk.
6. `n` - new partion -> `p` - primary partion -> `1` -> partion number -> `Enter`-> first celinder -> `Enter` last celinder -> make the whole disk as a partion -> `w` - write the partion table to disk and quit. 
7. `sudo partprobe /dev/sda` - make it recognized by linux kernel.
8. `mkdir /home/pi/mydata` - create mounting directory.
9. `sudo mkfs.ext4 /dev/sda1` - format partion `/dev/sda1` to `ext4` type which support `journal` on data saving.
10. `sudo mount -t ext4 /dev/sda1 /home/pi/mydata` - mount the partion to mount point so that we can access it.
11. `sudo chmod -R 777 /home/pi/mydata` - Set premission to the folder so that we can write and read date to disk.
12. `sudo mount -a` - Test automount.
13.  `df -Th` - Check if there is a partion has been mounted on /home/pi/mydata.
### Some Explanations
* The `defaults` mount option will give users read and write access to the file system.
* The value of `dump` field is usually zero.
* The `pass` field is used by the fsck program to determine the order in which filesystem checks are done at reboot time. As you can see in this file, the value of the pass field for the root file system is 1. Swap partitions do not need to be checked and the value for them is zero. All other file systems should have a value of 2. So I set the pass value as 2 for my drive.
