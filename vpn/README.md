# Raspberry Pi VPN
# Software PiVPN - WireGuard - NoIP
<!--ts-->
   * [Objective](#Objective)
   * [Installation](#Installation)
     * [Pi_setup](#Pi_setup)
     * [Pi_update](#Pi_update)
     * [Configure_netword](#Configure_netword)
     * [PiVPN](#PiVPN)
     * [NoIP](#NoIP)
     * [WireGuard](#WireGuard)
     * [Configure_netword](#Optional)
   * [Sources](#Sources)
<!--te-->

# Objective
The goal of this project is to establish a secure connection to your home network.

# Installation
You'll need three types of software for the project and a raspberry pi (I used Pi version 3B)

# Pi_setup
1. Raspberry Pi imager - 
[Pi Software General link](https://www.raspberrypi.com/software/)
[Pi Imager Softwar](https://www.raspberrypi.com/software/#:~:text=Raspberry%20Pi%20Imager.-,Download%20for%20macOS,-Download%20for%20Windows)
- Choose the first option Raspberry Pi OS (32-bit)
2. Insert and choose SD Card to flash
3. Write and confirm - est. 2-5 minutes
4. Create ssh file inside the pi boot folder
```bash
cd /Volumes/boot
touch ssh
```
4. Plug sd & ethernet into pi - 1-2 minute wait to setup

# Pi_update
1. Open the admin page for your router/IPS app
2. Find device IP address
3. ssh into the pi
```bash
ssh pi@device_ip
password: raspberry
```
4. Update pi & change the password
```bash
passwd
sudo apt update && sudo apt full-upgrade
sudo apt autoremove
sudo reboot
```
5. Log back into pi with the new password

# Configure_netword
1. Open the admin page for your router/IPS app - I had to use both for Cox
2. Navigate to connected devices - mine was raspberrypi
3. Edit DHCP/Reserved IP giving the pi a static IP address (keep the same one you use to remote into earlier)
4. Configure a none standard port forward to the static IP you just created for the device

# PiVPN
1. log in to your Raspberry Pi via SSH
2. Run this command and an install wizard should pop up
```bash
curl -L https://install.pivpn.io | bash
```
3. Choose WireGuard - change to the port you choose earlier
4. Your choice in DNS
5. Reboot Pi
```bash
sudo reboot
```
# NoIP
0. Create an account on NoIP for a free DDNS
https://www.noip.com/
1. log in to your Raspberry Pi via SSH
```bash
mkdir /home/pi/noip
cd /home/pi/noip
wget https://www.noip.com/client/linux/noip-duc-linux.tar.gz
tar vzxf noip-duc-linux.tar.gz
cd noip-2.1.9-1
sudo make
sudo make install
```
2. Add username & password from NoIp
3. Update interval, between 5 and 30 minutes
```bash
sudo /usr/local/bin/noip2
```
4. Check if the process is running
```bash
sudo noip2 -S
```
5. Automate process - open cron and add to the end of file 
```bash
sudo crontab -e
```
-
@reboot /usr/local/bin/noip2
-
Ctrl+O ENTER Ctrl+X
```bash
sudo reboot
```
6. After reboot, you can check the NoIP service
```bash
sudo noip2 -S
```
# WireGuard
1. log in to your Raspberry Pi via SSH
2. Create client account - ex: mac-air, iPhone
```bash
pivpn add
```
3. Generate WireGuard QR code for mobile app if needed
```bash
pivpn -qr <profile_name>
```
4. Remove profile if needed or
```bash
pivpn remove <profile_name>
```

# Sources

[Medium](https://medium.com/@timebarrier/install-pivpn-with-wireguard-on-a-raspberry-pi-with-pihole-19d95ba8d206)
[Blog Post](https://www.joshualowcock.com/guide/how-to-setup-raspberry-pi-with-pivpn-wireguard-and-noip-com/)