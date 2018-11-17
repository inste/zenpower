# Zenpower
Zenpower is Linux kernel driver for reading temperature, voltage, current and power for AMD Zen family CPUs.

## Installation
You can install this module via dkms.

### Installation commands for Ubuntu
```
sudo apt install dkms git build-essential linux-headers-$(uname -r)
cd ~
git clone https://github.com/ocerman/zenpower.git
cd zenpower
sudo make dkms-install
```

## Module activation
Because zenpower is using same PCI device as k10temp, you have to disable k10temp first.

1. Check if k10temp is active. `lsmod | grep k10temp`
2. Unload k10temp `sudo modprobe -r k10temp`
3. (optional) blacklist k10temp: `sudo bash -c 'sudo echo -e "\n# replaced with zenpower\nblacklist k10temp" >> /etc/modprobe.d/blacklist.conf'`
4. Activate zenpower `sudo modprobe zenpower`

## Sensors monitoring
You can use this script: [zenmonitor](https://github.com/ocerman/zenmonitor), or your favourie sensors monitoring software