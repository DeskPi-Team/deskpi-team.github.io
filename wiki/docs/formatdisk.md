
## Getting Start  
![DeskPi Pro](imgs/DeskPi logo.png).

For order please visit: [DeskPi.com](https://www.deskpi.com/).

## How to format a partition in command line.

* For `ext4` file system: 
```bash
sudo mkfs.ext4 /dev/sda1
```
- Format partion `/dev/sda1` to `ext4` type which support `journal` on data saving.

* For `vfat` format file system:
```bash
sudo mkfs.vfat /dev/sda1
```
- Format partion `/dev/sda1` into `vfat` type which means `virtual file allocation table`.
