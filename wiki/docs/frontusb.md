
## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## How to enable front USB ports on DeskPi Pro.
* There are `two` ways to enable the front USB ports on DeskPi Pro.
- 1. Install deskpi driver will enable front USB ports automatically.
- 2. Edit /boot/config.txt file and add following line:
```bash
dtoverlay=dwc2,dr_mode=host
```
It need to `reboot` Raspberry Pi to take effect.
