Pi Ubuntu server - Setup
# How to install Ubuntu Server on your Raspberry Pi | Ubuntu
https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview
1. RB-Pi Imager
    - Ubuntu server 20.04 64-bit
2. Connect SD, Ethernet, monitor, key board, then power
    - Let it run for 2 minutes - cloud-int set up
    - Change password - ubuntu > password
3. On RP-Pi run - ip address
    - Item 2 - Eth0 = net 192.168.0.25
4. SSH in Pi
    - ssh ubuntu@192.168.0.25
    - ssh ubuntu@192.168.0.104
    - Type y
    - sudo apt update
    - sudo apt upgrade 
    - sudo reboot
    - ssh ubuntu@192.168.0.25