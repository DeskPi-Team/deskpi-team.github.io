## FAQ List 

## OS Issues 
### What operating systems are currently tested on DeskPi Pro and works fine?

* `Raspbian OS` - 32bit version: 2020-08-12 [Raspberry Pi OS](https://www.raspberrypi.org/software/operating-systems/).
* `Ubuntu-mate OS` - 32bit version:20.04.1-desktop--armhf+raspi [Ubuntu mate 20.04 LTS 32Bit](https://releases.ubuntu-mate.org/focal/armhf/ubuntu-mate-20.04.1-desktop-armhf+raspi.img.xz).
* `Manjaro OS` - 32bit verison: 20.2 [Manjaro XFCE 20.2](https://manjaro.org/downloads/official/xfce/)
* `Kali-linux-arm OS` - 32bit version: 2020.4 [Kali Linux RaspberryPi 2, 3, 4 and 400](https://www.offensive-security.com/kali-linux-arm-images/).

### Dose it support 64bit OS such as Ubuntu 20.10? 
* It depends on Raspberry Pi offical support, we suggest that you can refer to offical source here:[Raspberry Pi OS](https://www.raspberrypi.org/software/operating-systems/).

## Front USB Issues 
### Why the USB on the front panel of my DESKPI cannot be used? I have burned the system many times?

* Please check your /boot/config.txt file and make sure it contains `dtoverlay=dwc2,dr_mode=host`, and if you add it by yourself, it need to reboot Raspberry Pi to take effect.


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
```
  1. Open a terminal or press "Ctrl+Alt+T".
  2. Typing: "sudo fdisk -l" to check if the disk has been recognized or typing: "sudo lsusb -t", typing: "dmesg |grep -i usb" to make sure disk has been connected.
  3. If the disk can be found by those commands, manually format and mount the partition:  
   for example: 
   3.1 `sudo fdisk /dev/sda` - sda means my first SCSI type disk which recognized by my system.
   3.2 `p` - typing `p` means print current partions that contains on the disk.
   3.3 `n` - new partion -> `p` - primary partion -> `1` -> partion number -> `Enter`-> first celinder -> `Enter` last celinder -> make the whole disk as a partion -> `w` - write the partion table to disk and quit. 
   3.4 `sudo partprobe /dev/sda` - make it recognized by linux kernel.
   3.5 `mkdir /home/pi/mydata` - create mounting directory.
   3.6 `sudo mkfs.ext4 /dev/sda1` - format partion `/dev/sda1` to `ext4` type which support `journal` on data saving.
   3.7 `sudo mount -t ext4 /dev/sda1 /home/pi/mydata` - mount the partion to mount point so that we can access it.
   3.8 `sudo chmod -R 777 /home/pi/mydata` - Set premission to the folder so that we can write and read date to disk.
  4. How To Automount File Systems on Raspbian(Linux)
   4.1 `sudo blkid` - Get the Name, In the output of this command, the first column is the name of your drives. The second column is the label of the drive (if you set a label for it) and the third column is the UUID of your drives.
First you need to know the name of the drive that is going to be automatically mounted. 
   4.2 `sudo nano /etc/fstab` - [Dangerous] If the operation fails, the system will not start, add your partion information and let it auto mount after rebooting, We need to append one line of code at the end of the file. The format of this line of code is as follows:
`UUID=<uuid-of-your-drive>  <mount-point>  <file-system-type>  <mount-option>  <dump>  <pass>`
* Note that you need to separate these items with `Tab key`. For example, I added the following line to the end of /etc/fstab.
`UUID=eb67c479-962f-4bcc-b3fe-cefaf908f01e  /home/pi/mydata  ext4  defaults  0  2`
Save and close the file. Then run the following command to see if it works.
* `sudo mount -a` - Test automount.
* `df -Th` - Check if there is a partion has been mounted on /home/pi/mydata.
```
### Some Explanations
* The `defaults` mount option will give users read and write access to the file system.
* The value of `dump` field is usually zero.
* The `pass` field is used by the fsck program to determine the order in which filesystem checks are done at reboot time. As you can see in this file, the value of the pass field for the root file system is 1. Swap partitions do not need to be checked and the value for them is zero. All other file systems should have a value of 2. So I set the pass value as 2 for my drive.

## HDMI issue
### My screen goes to black when I was booting up my deskpi. 

* Please try to shift HDMI cable from HDMI0 to HDMI1 which is beside 3.5mm audio jack and try again.

## USB booting
### Why does it take so much time when I boot it from USB booting?

* It seems to be some tough question, some issues may caused by the usb controller chip performance issue.

