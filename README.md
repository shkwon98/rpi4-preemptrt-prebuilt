# (Pre-built) Raspberry Pi 4 Preempt-RT Patch
These steps will help you through the installation of preempt-rt on the **Raspberry Pi 4**. The kernel that is used is the 4.19.86 linux kernel.

* This is a simplified version of [rpi4_preemptRT](https://github.com/shkwon98/rpi4_preemptRT) repository.
* It contains additional support as an option to use W5500 Ethernet network driver for users who need extra ethernet port on raspberry pi.
<br>



## Requirements:
* Raspberry Pi 4
* (Option) WIZnet W5500 Ethernet chip with SPI interface

> Create a new raspbian image on the micro-SDcard with the Pi imager. Use the file on the link below.<br>
> [2020-02-13-raspbian-buster.zip](http://downloads.raspberrypi.org/raspbian/images/raspbian-2020-02-14/2020-02-13-raspbian-buster.zip)<br>
<br>



## A. Installing the preempt-rt on the Raspberry pi

1. Download the pre-built kernel
```console
pi@raspberrypi:~$ cd /tmp
pi@raspberrypi:/tmp$ wget -O RTkernel_W5500.tgz https://github.com/shkwon98/rpi4_preemptRT_pre-built/blob/main/RTkernel_W5500.tgz?raw=true
```

2. Inside the raspberry pi, unpack the .tgz and copy it
```console
pi@raspberrypi:/tmp$ tar xzf RTkernel_W5500.tgz
pi@raspberrypi:/tmp$ cd boot
pi@raspberrypi:/tmp/boot$ sudo cp -rd * /boot/
pi@raspberrypi:/tmp/boot$ cd ../lib
pi@raspberrypi:/tmp/lib$ sudo cp -rd * /lib/
pi@raspberrypi:/tmp/lib$ cd ../overlays
pi@raspberrypi:/tmp/overlays$ sudo cp -d * /boot/overlays
pi@raspberrypi:/tmp/overlays$ cd ..
pi@raspberrypi:/tmp$ sudo cp -d bcm* /boot/
```

3. Edit the boot configutarion
```console
pi@raspberrypi:/tmp$ sudo nano /boot/config.txt
```
> Add in the beginning:
```
kernel=kernel7l.img
```
> (Option) Type in the last line:
```
dtoverlay=w5500
```

4. Reboot and check the patched kernel
```console
pi@raspberrypi:/tmp$ sudo reboot
pi@raspberrypi:~$ uname -r
```

<br>

## BENCHMARK:
* [Cyclictest benchmark](https://github.com/shkwon98/Cyclictest)
