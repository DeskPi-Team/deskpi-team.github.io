
## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## what is deskpi-config tool

* `deskpi-config` tool is a tool like `raspi-config` tool, it is a shell script for you to change deskpi fan behavior. 

* You can use this command to keep your fan spinning at 100% speed, you can also use it to stop spinning the fan, and you can also control the rotation speed of the fan by adjusting the threshold. This depends entirely on your preference. If you like to be quieter, You can turn off the fan. If under high load, you can use 100% speed for heat dissipation.

## How to control fan speed mannualy.

* Open a terminal and typing following command:

```bash
deskpi-config
```
* Input the number you select and setup fan behavior according the information it shows up.

### Option explanation
* The number from 1 to 4 is to setting your fan speed to a static level.
* Number 5 is just turn off the fan.
* Number 6 is to guide you to create a file located to /etc/deskpi.conf and you
can specify the threshold of temperature and fan speed level according to your
idea, once the file has been created, the program will according to the
configuration file to setup your fan.
* Number 7 is to enable automatic fan control by default paramaters. 

** Default arguments:  
```
TEMP   : Fan_SPEED_LEVEL
<40C   : 0%  
40~50C : 25%  
50~65C : 50%  
65~75C : 75%  
>75C   : 100%  
```
* If you set the wrong config, just re-execute this command again.
