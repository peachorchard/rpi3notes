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
