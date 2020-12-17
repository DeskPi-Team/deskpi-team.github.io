## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## Front USB Issues 
### Why the USB on the front panel of my DESKPI cannot be used? I have burned the system many times?

* Please check your /boot/config.txt file and make sure it contains `dtoverlay=dwc2,dr_mode=host`, and if you add it by yourself, it need to reboot Raspberry Pi to take effect.
* Just install deskpi driver.
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
