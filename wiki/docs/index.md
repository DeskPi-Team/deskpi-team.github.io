## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## Hardware assemble tutorial

* Tutorial video: [DeskPi Pro hardware assembling tutorial 1080P](https://youtu.be/MB76Lt0VXuo).

## Software Configuration 

* USB booting: [How to USB boot your Raspberry Pi via DeskPi Pro with M 2 SATA SSD 1080p](https://youtu.be/wUHZb9E_WDQ).

## Supported OS
* `Raspbian OS` - 32bit version: 2020-08-12 [Raspberry Pi OS](https://www.raspberrypi.org/software/operating-systems/).
* `Ubuntu-mate OS` - 32bit version:20.04.1-desktop--armhf+raspi [Ubuntu mate 20.04 LTS 32Bit](https://releases.ubuntu-mate.org/focal/armhf/ubuntu-mate-20.04.1-desktop-armhf+raspi.img.xz).
* `Manjaro OS` - 32bit verison: 20.2 [Manjaro XFCE 20.2](https://manjaro.org/downloads/official/xfce/)
* `Kali-linux-arm OS` - 32bit version: 2020.4 [Kali Linux RaspberryPi 2, 3, 4 and 400](https://www.offensive-security.com/kali-linux-arm-images/).

## Install Deskpi driver

* 1. Flash the latest version of `supported OS` to your TF(microSD) card with etcher flash imaging tool 
* 2. Insert TF(MicroSD) card to DeskPi card slot and connect the power supply(which come with the package.)
* 3. Connect DeskPi to internet. (You need to configure WLAN country in order to enable Wi-Fi adapter) 
* 4. Open a terminal by press icon on the task bar or just press "Ctrl+alt+T.
* 5. Typing those command to install the driver automatically.(Raspberry Pi will reboot after installing.)

### For Raspbian and RetroPie OS.
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install.sh
sudo ./install.sh
```
### For Ubuntu-mate OS
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install-ubuntu-mate.sh
sudo ./install-ubuntu-mate.sh
```
### For Manjaro OS
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install-manjaro.sh
sudo ./install-manjaro.sh
```
### For Kali-linux-arm OS.
* Image Download URL: https://images.kali.org/arm-images/kali-linux-2020.3a-rpi3-nexmon.img.xz <br>
```bash
cd ~
git clone https://github.com/DeskPi-Team/deskpi.git
cd ~/deskpi/
chmod +x install-kali.sh
sudo ./install-kali.sh
```
## How to Uninstall deskpi 
```bash
DeskPi-uninstall 
```
And then select the number against to your OS Type.

### For Windows IoT OS
* Unsupported due to lacking of driver.
* Testing version: Midnight falcon

## How to boot from USB SSD/HDD?
After initial Raspberry Pi Configuration and once you have Internet Connectivity established, Install the DeskPi Pro Utilities from `https://github.com/DeskPi-Team/deskpi.git`
Open a Terminal / Console and run the following commands:  
```bash 
sudo apt update
sudo apt full-upgrade
sudo rpi-update
```
When complete, run:
```bash
sudo reboot
```
Upon reboot, open Terminal again:
```bash
sudo raspi-config
```
* go to Advanced Options 
* Select Boot Order, select #1 `USB Boot`, Return to Advanced Options,
* Select Boot Loader Version, choose `Latest Version`
* Save & exit
### Reboot again (to restart with new settings)
```bash
sudo reboot 
```
After reboot, re-open Terminal again
```bash
sudo -E rpi-eeprom-config --edit
```
•	do not change anything, it is unnecessary
•	press Ctrl-X to save, answer Y to overwrite file.
```bash
sudo reboot    
```
Now you are ready to install Raspberry-OS onto your USB Boot Device.
You can use the Raspberry Imager from `www.raspberrypi.org` website. 
Depending on device the new SD Card Copier can transfer the SD-Card image to the USB Device (ensure you select generate a new UUID). 
Once your USB drive is imaged & ready to boot, shutdown your Deskpi-Pro, remove the SD-Card and power-up to boot from the USB Boot drive, once running & configured you can install your additional software and proceed as usual. 

## How to Use IR function onboard.
* 1. You need to enable `gpio-ir` function by modify `/boot/config.txt` file. uncomment this line if not exsit please add it.
```bash
dtoverlay=gpio-ir,gpio_pin=17 
```
* 2. Install `lirc` package:
```bash
sudo apt-get install lirc
```
* 3. Modify configuration file on location: /etc/lirc/lirc_options.conf and make sure it has following parameters:
```bash
driver          = default
device          = /dev/lirc0
```
* 4. Reboot your Raspberry Pi and test it with following command:
```bash
mode2 -d /dev/lirc1
```
## deskpi-config tool

* `deskpi-config` tool is a tool like `raspi-config` tool, it is a shell script for you to change deskpi fan behavior. 
* You can use this command to keep your fan spinning at 100% speed, you can also use it to stop spinning the fan, and you can also control the rotation speed of the fan by adjusting the threshold. This depends entirely on your preference. If you like to be quieter, You can turn off the fan. If under high load, you can use 100% speed for heat dissipation.

