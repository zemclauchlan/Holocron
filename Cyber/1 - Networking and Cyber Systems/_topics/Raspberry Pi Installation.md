The goal is to install a fresh new installation of Raspberry Pi OS onto a SD card.
    
# Flash SD Card

Run `Raspberry Pi Imager` on your PC/laptop. 

If it’s not installed, get it from here: [https://www.raspberrypi.com/software/](https://www.raspberrypi.com/software/)


<img src="https://www.notion.so/icons/condense_gray.svg" alt="https://www.notion.so/icons/condense_gray.svg" width="40px" /> Take a screenshot of this instructions below for VET Competency ICTICT213 - 1.3


<img src="https://www.notion.so/icons/condense_gray.svg" alt="https://www.notion.so/icons/condense_gray.svg" width="40px" /> Take a screenshot of this instructions below for VET Competency ICTICT213 - 2.2

![[rpiImager.png]]

Choose the Raspberry Pi Device that you have been assigned. *Most likely* **Raspberry Pi 4** will be the correct option.
![[rpiImagerDevice.png]]


Insert the SD card into the computer or a Card Reader attached to your computer. Run through the Wizard, making sure to choose the **Raspberry Pi OS (64-bit)** Operating System.
![[rpiImagerOS.png]]

Choose the SD card as the Storage option.

Click Next. You may need to enter an administrator password

Wait for the process to complete. This could take 10-20 minutes depending on the speed of the device.

# Boot into the Raspberry Pi

Insert the SD card into the Raspberry Pi. Attach the Monitor, Keyboard and Mouse as appropriate. Finally, add power and turn on. The Operating System should boot.
    
    
# Update the system


>💡 Take a screenshot of these instructions below for VET Competency ICTICT213 - 2.4


First set the time to the current time

`sudo date -s "Thu 14 Mar 2024 1300"`

## **Update Software and Configuration**

Run the following commands at the terminal. Press Enter after each command.

```bash
cd Documents
git clone http://github.com/Lake-Tuggeranong-College/RPi
cd RPi
chmod +x rpi-setup.sh
sudo ./rpi-setup.sh
```

# Configure the time service

💡 Take a screenshot of these instructions below for VET Competency ICTICT213 - 3.1


After updating the system, open the terminal.

enter the following commands

```bash
sudo apt install ntp ntpdate
sudo service ntp stop
sudo ntpdate 203.62.5.5
sudo service ntp start
```
    
    
    
# RPi Web Server

## Installation


<img src="https://www.notion.so/icons/condense_gray.svg" alt="https://www.notion.so/icons/condense_gray.svg" width="40px" /> Take a screenshot of this instructions below for VET Competency ICTICT213 - 2.5


# RPi - installing Software

## Install VS Code extensions

within Visual Studio Code, install the following extensions:

- PlatformIO IDE
- PHP Server
- Database Client JDBC (by Weijan Chen)
- MySQL (by Weijan Chen)