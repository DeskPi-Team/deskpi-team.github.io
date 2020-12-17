
## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

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
