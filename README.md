# rpi3notes
Raspberry PI 3 notes

# Headless Setup
## Raspbian SD Creation
1. Download Raspbian
(https://www.raspberrypi.org/downloads/raspbian)
2. Unzip to get the .img file
3. Find out the block device for the SD card (/dev/mmcblk0, etc.)
4. Unmount the SD card partitions
5. 

   ```bash
sudo dd bs=4M if=raspbian.img of=/dev/mmcblk0
sudo sync
   ```

6. 

   ```
#/etc/wpa_supplicant/wpa_supplicant.conf
network={
ssid="ESSID"
psk="Your_wifi_password"
}
   ```

7. 

   ```bash
# to start ssh at boot
touch /boot/ssh
   ```

8. Unmount the SD card
9. Put the SD card into the PI
10. Power up the PI

## First Boot
1. 

   ```bash
ssh pi@raspberrypi.local
raspi-conf
   ```

2. Change the name of the pi
3. Change the password for pi using `passwd`

## Cross Compile from Ubuntu
1. 

   ```bash
sudo apt-get install build-essential
sudo apt-get install g++-arm-linux-gnueabihf
sudo apt-get install gdb-multiarch
   ```
   
2. 

   ```bash
arm-linux-gnueabihf-g++ -O3 -g3 -Wall -c -o -fPIC "h.o" "h.cpp"
arm-linux-gnueabihf-g++ -o "hello" h.o
   ```

## Remote Debugging
1. 

   ```bash
# on the PI
sudo apt-get install gdbserver
   ```

2. 

   ```bash
# on the PI
gdbserver --multi nameofpi:2001
   ```
   
3. 

   ```bash
# on the laptop/desktop
gdb-multiarch
# in gdb on the laptop/desktop
target extended-remote nameofpi.local:2001
set remote exec-file pathincludingexe
file exenamewithoutpath
run
   ```
