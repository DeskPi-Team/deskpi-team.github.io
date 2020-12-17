
## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## How to mount partition to mount point:
* Create a directory(folder) as mounting point.
```bash
mkdir /home/pi/mydata
```
- create mounting directory.
* Mount a partition to mounting point.
```bash
sudo mount -t ext4 /dev/sda1 /home/pi/mydata
```
- mount the partion to mount point so that we can access it.

* Modify the permission to the mounting point.
```bash
sudo chmod -R 777 /home/pi/mydata
```
- Set premission to the folder so that we can write and read date to disk.

### How To Automount File Systems on Raspbian(Linux)
* Get the Name, In the output of this command, the first column is the name of your drives. The second column is the label of the drive (if you set a label for it) and the third column is the UUID of your drives.
```bash
sudo blkid
```
* First you need to know the name of the drive that is going to be automatically mounted. 
```bash
sudo nano /etc/fstab
```
* [`Dangerous`] If the operation fails, the system will not start, add your partion information and let it auto mount after rebooting, We need to append one line of code at the end of the file. 
* The format of this line of code is as follows:
```bash 
UUID=<uuid-of-your-drive>  <mount-point>  <file-system-type>  <mount-option>  <dump>  <pass>
```
* Note that you need to separate these items with `Tab key`. 
* For example, I added the following line to the end of /etc/fstab.
```bash
UUID=eb67c479-962f-4bcc-b3fe-cefaf908f01e  /home/pi/mydata  ext4  defaults  0  2
```
* Save and close the file. 
* Then run the following command to see if it works.
```bash
sudo mount -a
```
- Test automount.
```bash 
df -Th
```
- Check if there is a partion has been mounted on /home/pi/mydata.
### Some Explanations
* The `defaults` mount option will give users read and write access to the file system.
* The value of `dump` field is usually zero.
* The `pass` field is used by the fsck program to determine the order in which filesystem checks are done at reboot time. As you can see in this file, the value of the pass field for the root file system is 1. Swap partitions do not need to be checked and the value for them is zero.
* All other file systems should have a value of 2. 
