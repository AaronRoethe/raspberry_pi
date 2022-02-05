# Kali Install
source: [link]("https://www.golinuxcloud.com/kali-linux-on-raspberry-pi/")

# Requirements
Raspberry Pi board (2, 3, or 4)
Power supply
Micro SD card (at least 8GB)
Internet access - ethernet
[Pi Imager Software](https://www.raspberrypi.com/software/#:~:text=Raspberry%20Pi%20Imager.-,Download%20for%20macOS,-Download%20for%20Windows)

# Steps
# 1 Download kali installer
```bash
wget https://kali.download/arm-images/kali-2021.4/kali-linux-2021.4-rpi-armhf.img.xz
```
# 2 Flash installer on SD card
Open Pi Imager select file just downloaded & instert Micro SD card to flash.
# 3 Boot kali-pi
Plug in ethernet & SD card, power on device - est. 2 minutes

# 4 Find device ip-address
I use the basic admin portal on my router. Search inside your internet browser http://192.168.0.1 (My ISP is Ciox) your admin page may have a different address. Navigate to connected devices and it should appear under kali-rpi. Set a static IP to something you'll remeber.

# 4 SSH into kali
Open terminal of choice.
```bash
ssh kali@<ip-address>
password = kali
```
# optional 
Run a few commad to test out your new project! 
```bash
nmap -A <target ip-address>
```

# add docker screamed to browser next!
Using Docker:
```bash
docker run --user root --rm  -it --shm-size=512m -p 6901:6901 -e VNC_PW=password kasmweb/core-kali-rolling:develop-rolling
```
In web-browser search https://localhost:6901