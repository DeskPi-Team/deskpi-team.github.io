
## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## How to boot from USB SSD/HDD?
After initial Raspberry Pi Configuration and once you have Internet Connectivity established, Install the DeskPi Pro Utilities from `https://github.com/DeskPi-Team/deskpi.git`
* Open a Terminal / Console and run the following commands:  
```bash 
sudo apt update
sudo apt full-upgrade
sudo rpi-update
```
* When complete, run:
```bash
sudo reboot
```
* Upon reboot, open Terminal again:
```bash
sudo raspi-config
```
* go to Advanced Options 
* Select Boot Order, select #1 `USB Boot`, Return to Advanced Options,
* Select Boot Loader Version, choose `Latest Version`
* Save & exit
* Reboot again (to restart with new settings)
```bash
sudo reboot 
```
After reboot, re-open Terminal again
```bash
sudo -E rpi-eeprom-config --edit
```
• Do not change anything, it is unnecessary
• Press `Ctrl-X` to save, answer `Y` to overwrite file.
```bash
sudo reboot    
```
* Now you are ready to install Raspberry-OS onto your USB Boot Device.
You can use the Raspberry Imager from `www.raspberrypi.org` website. 
Depending on device the new SD Card Copier can transfer the SD-Card image to the USB Device (ensure you select generate a new UUID). 
Once your USB drive is imaged & ready to boot, shutdown your Deskpi-Pro, remove the SD-Card and power-up to boot from the USB Boot drive, once running & configured you can install your additional software and proceed as usual. 
