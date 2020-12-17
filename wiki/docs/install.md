## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## Install Deskpi driver

* 1. Flash the latest version of `supported OS` to your TF(microSD) card with etcher flash imaging tool 
* 2. Insert TF(MicroSD) card to DeskPi card slot and connect the power supply(which come with the package.)
* 3. Connect DeskPi to internet. (You need to configure WLAN country in order to enable Wi-Fi adapter) 
* 4. Open a terminal by press icon on the task bar or just press "Ctrl+alt+T".
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
