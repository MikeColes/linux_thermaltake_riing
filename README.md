# Linux driver and daemon for Thermaltake Riing


## Compatibility
Python3 only.

Currently supported devices are (as they show up in thermaltakes TTRGBPLUS software:  
    Flow Riing RGB  
    Lumi Plus LED Strip  
    Pacific PR22-D5 Plus  
    Pacific Rad Plus LED Panel  
    Pacific V-GTX 1080Ti Plus GPU Waterblock  
    Pacific W4 Plus CPU Waterblock  
    Riing Plus  
If your's isn't listed, please create an issue and I'll implement it ASAP!!  


## Installation

### Pypi

`sudo pip3 install linux_thermaltake_rgb`  
The setup file will create the systemd user unit, and udev rule 
in `/usr/share/linux_thermaltake_rgb`  
you will need to copy these to the appropriate locations:

```bash
sudo cp /usr/share/linux_thermaltake_rgb/90-linux_thermaltake_rgb.rules /etc/udev/rules.d/
sudo cp /usr/share/linux_thermaltake_rgb/linux-thermaltake-rgb.service /usr/lib/systemd/user/

# and if this is a fresh install copy the default config file:
sudo cp /usr/share/linux_thermaltake_rgb/config.yml /etc/linux_thermaltake_rgb/
```

then add your user to the `plugdev` group - `sudo usermod -a -G plugdev <user>`  

then reconnect your device.  
  note: you may need to log out and back in so your user is recognised as being in the `plugdev` group  
  
### Arch linux

available in the aur as `linux-thermaltake-rgb`

### starting and enabling the daemon

start and enable the systemd service  
`systemctl --user start linux-thermaltake-rgb.service; systemctl --user enable linux-thermaltake-rgb.service`  


## Configuration
the configuration file is expected to be in: `/etc/linux_thermaltake_rgb/config.yml`  
edit and configure suitably.  

example config is in `linux_thermaltake_rgb/assets/config.yml`
